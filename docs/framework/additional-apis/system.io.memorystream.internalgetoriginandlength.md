---
title: Elementu MemoryStream. InternalGetOriginAndLength — Metoda (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284032"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="fe586-102">Elementu MemoryStream. InternalGetOriginAndLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe586-102">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="fe586-103">Pobiera wewnętrzne wartości źródłowe i długość strumienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="fe586-103">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="fe586-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe586-104">Parameters</span></span>

- <span data-ttu-id="fe586-105">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="fe586-105">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="fe586-106">Gdy ta metoda zwraca, przesunięcie tablicy bajtowej określonej podczas tworzenia nowego obiektu <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="fe586-106">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="fe586-107">Zawiera wartość 0, jeśli tablica bajtów została utworzona przez <xref:System.IO.MemoryStream>.</span><span class="sxs-lookup"><span data-stu-id="fe586-107">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="fe586-108">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="fe586-108">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="fe586-109">Gdy ta metoda zwraca, liczba bajtów w strumieniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="fe586-109">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe586-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe586-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="fe586-111">Metoda `MemoryStream.InternalGetOriginAndLength` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fe586-111">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fe586-112">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="fe586-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe586-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe586-113">Requirements</span></span>

<span data-ttu-id="fe586-114">**Przestrzeń nazw:** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="fe586-114">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="fe586-115">**Zestaw:** mscorlib. dll (w bibliotece Mscorlib. dll)</span><span class="sxs-lookup"><span data-stu-id="fe586-115">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="fe586-116">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="fe586-116">**.NET Framework versions:** Available since 2.0.</span></span>
