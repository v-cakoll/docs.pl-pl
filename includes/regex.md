---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802857"
---

> [!WARNING]
> <span data-ttu-id="57781-101">Podczas używania <xref:System.Text.RegularExpressions> do przetwarzania niezaufanych danych wejściowych należy przekazać limit czasu.</span><span class="sxs-lookup"><span data-stu-id="57781-101">When using <xref:System.Text.RegularExpressions> to process untrusted input, pass a timeout.</span></span> <span data-ttu-id="57781-102">Złośliwy użytkownik może podać dane wejściowe, aby `RegularExpressions` spowodować [atak typu "odmowa usługi"](https://www.us-cert.gov/ncas/tips/ST04-015).</span><span class="sxs-lookup"><span data-stu-id="57781-102">A malicious user can provide input to `RegularExpressions` causing a [Denial-of-Service attack](https://www.us-cert.gov/ncas/tips/ST04-015).</span></span> <span data-ttu-id="57781-103">Interfejsy API środowiska ASP.NET Core Framework, które używają `RegularExpressions` przekazywania limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="57781-103">ASP.NET Core framework APIs that use `RegularExpressions` pass a timeout.</span></span>
