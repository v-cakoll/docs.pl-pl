---
title: COR_ARRAY_LAYOUT — Struktury
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179351"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="c4bcd-102">COR_ARRAY_LAYOUT — Struktury</span><span class="sxs-lookup"><span data-stu-id="c4bcd-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="c4bcd-103">Zawiera informacje o układzie obiektu tablicowego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4bcd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4bcd-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="c4bcd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c4bcd-105">Members</span></span>  
  
|<span data-ttu-id="c4bcd-106">Członek</span><span class="sxs-lookup"><span data-stu-id="c4bcd-106">Member</span></span>|<span data-ttu-id="c4bcd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c4bcd-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="c4bcd-108">Identyfikator typu obiektów, które zawiera tablica.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="c4bcd-109">A CorElementType wartość wyliczenia, która wskazuje, czy składnik jest odwołanie do wyrzucania elementów bezużytecznych, klasy wartości lub pierwotne.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="c4bcd-110">Przesunięcie do pierwszego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="c4bcd-111">Rozmiar każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="c4bcd-112">Przesunięcie do liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="c4bcd-113">Rozmiar rangi w bajtach.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="c4bcd-114">Liczba szeregów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="c4bcd-115">Przesunięcie, od którego zaczynają się rangi.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4bcd-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4bcd-116">Remarks</span></span>  
 <span data-ttu-id="c4bcd-117">Pole `rankSize` określa rozmiar rangi w tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="c4bcd-118">Jest to dokładne dla tablic jednowymiarowych, jak również.</span><span class="sxs-lookup"><span data-stu-id="c4bcd-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="c4bcd-119">Wartość `numRanks` wynosi 1 dla tablicy jednowymiarowej i `N` wielowymiarowej tablicy wymiarów. `N`</span><span class="sxs-lookup"><span data-stu-id="c4bcd-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4bcd-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4bcd-120">Requirements</span></span>  
 <span data-ttu-id="c4bcd-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4bcd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4bcd-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4bcd-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4bcd-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4bcd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4bcd-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4bcd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4bcd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4bcd-125">See also</span></span>

- [<span data-ttu-id="c4bcd-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c4bcd-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c4bcd-127">Debugging</span><span class="sxs-lookup"><span data-stu-id="c4bcd-127">Debugging</span></span>](index.md)
