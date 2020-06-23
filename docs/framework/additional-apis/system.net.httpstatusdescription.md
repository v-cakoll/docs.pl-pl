---
title: HttpStatusDescription, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990391"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="63c1d-102">HttpStatusDescription, klasa</span><span class="sxs-lookup"><span data-stu-id="63c1d-102">HttpStatusDescription class</span></span>

<span data-ttu-id="63c1d-103">Zawiera standardowe opisy stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63c1d-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="63c1d-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="63c1d-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="63c1d-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="63c1d-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="63c1d-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="63c1d-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="63c1d-107">Metoda Get</span><span class="sxs-lookup"><span data-stu-id="63c1d-107">Get method</span></span>

<span data-ttu-id="63c1d-108">Zwraca opis skojarzony z określonym kodem stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63c1d-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="63c1d-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="63c1d-109">Parameters</span></span>

<span data-ttu-id="63c1d-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="63c1d-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="63c1d-111">Kod stanu HTTP, na przykład `404` .</span><span class="sxs-lookup"><span data-stu-id="63c1d-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="63c1d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="63c1d-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="63c1d-113">Opis stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63c1d-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="63c1d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63c1d-114">Requirements</span></span>

<span data-ttu-id="63c1d-115">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="63c1d-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="63c1d-116">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="63c1d-116">**Assembly:** System (in System.dll)</span></span>
