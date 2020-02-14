---
title: Exception. PrepForRemoting — Metoda (system)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214898"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="389b1-102">Metoda Exception.PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="389b1-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="389b1-103">Zachowuje ślad stosu po stronie serwera, dołączając go do wiadomości przed ponownym wyrzucaniem wyjątku w lokacji wywołania klienta.</span><span class="sxs-lookup"><span data-stu-id="389b1-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="389b1-104">Zwraca</span><span class="sxs-lookup"><span data-stu-id="389b1-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="389b1-105">To wystąpienie <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="389b1-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="389b1-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="389b1-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="389b1-107">Metoda `Exception.PrepForRemoting` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="389b1-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="389b1-108">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="389b1-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="389b1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="389b1-109">Requirements</span></span>

<span data-ttu-id="389b1-110">**Przestrzeń nazw:** <xref:System></span><span class="sxs-lookup"><span data-stu-id="389b1-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="389b1-111">**Zestaw:** mscorlib. dll (w bibliotece Mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="389b1-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="389b1-112">**.NET Framework wersje:** Dostępne od 1,0.</span><span class="sxs-lookup"><span data-stu-id="389b1-112">**.NET Framework versions:** Available since 1.0.</span></span>
