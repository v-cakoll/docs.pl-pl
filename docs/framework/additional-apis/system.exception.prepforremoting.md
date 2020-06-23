---
title: Exception. PrepForRemoting — Metoda (system)
description: Przejrzyj metodę Exception. PrepForRemoting w programie .NET. Metoda dodaje ślad stosu po stronie serwera do komunikatu przed ponownym zgłoszeniem wyjątku na kliencie.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105262"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="42a90-104">Metoda Exception.PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="42a90-104">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="42a90-105">Zachowuje ślad stosu po stronie serwera, dołączając go do wiadomości przed ponownym wyrzucaniem wyjątku w lokacji wywołania klienta.</span><span class="sxs-lookup"><span data-stu-id="42a90-105">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="42a90-106">Zwraca</span><span class="sxs-lookup"><span data-stu-id="42a90-106">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="42a90-107">To <xref:System.Exception> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="42a90-107">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="42a90-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42a90-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="42a90-109">`Exception.PrepForRemoting`Metoda jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="42a90-109">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="42a90-110">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="42a90-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="42a90-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42a90-111">Requirements</span></span>

<span data-ttu-id="42a90-112">**Przestrzeń nazw:**<xref:System></span><span class="sxs-lookup"><span data-stu-id="42a90-112">**Namespace:** <xref:System></span></span>

<span data-ttu-id="42a90-113">**Zestaw:** mscorlib.dll (w mscorlib.dll)</span><span class="sxs-lookup"><span data-stu-id="42a90-113">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="42a90-114">**.NET Framework wersje:** Dostępne od 1,0.</span><span class="sxs-lookup"><span data-stu-id="42a90-114">**.NET Framework versions:** Available since 1.0.</span></span>
