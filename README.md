## NextJS API---> Pagination

### Prisma Cursor Pagination using findMany()
![](https://imgur.com/2HBdLAI.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.findMany({
            cursor: {
                id: "e28360d2-e6b4-447a-973f-ec4481291a32",
            },
            take: 2,
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### Prisma Pagination using skip & take
![](https://imgur.com/X1iMvgc.png)

```bash
const readData = await prisma.employee.findMany({
            skip: 1,
            take: 3,
        });
```
---
