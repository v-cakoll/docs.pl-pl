---
title: Exception. PrepForRemoting — Metoda (system)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405033"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="8b53e-102">Exception. PrepForRemoting, Metoda</span><span class="sxs-lookup"><span data-stu-id="8b53e-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="8b53e-103">Zachowuje ślad stosu po stronie serwera, dołączając go do wiadomości przed ponownym wyrzucaniem wyjątku w lokacji wywołania klienta.</span><span class="sxs-lookup"><span data-stu-id="8b53e-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="8b53e-104">Zwraca</span><span class="sxs-lookup"><span data-stu-id="8b53e-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="8b53e-105">To <xref:System.Exception> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8b53e-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b53e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b53e-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8b53e-107">Metoda `Exception.PrepForRemoting` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8b53e-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8b53e-108">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="8b53e-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b53e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b53e-109">Requirements</span></span>

<span data-ttu-id="8b53e-110">**Przestrzeń nazw:** <xref:System></span><span class="sxs-lookup"><span data-stu-id="8b53e-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="8b53e-111">**Zestaw:** mscorlib. dll (w bibliotece Mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="8b53e-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="8b53e-112">**.NET Framework wersje:** Dostępne od 1,0.</span><span class="sxs-lookup"><span data-stu-id="8b53e-112">**.NET Framework versions:** Available since 1.0.</span></span>
