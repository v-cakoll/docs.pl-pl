---
title: "COR_ARRAY_LAYOUT — Struktury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ARRAY_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ARRAY_LAYOUT
helpviewer_keywords: COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b936b1b2187ec68db7f5fdecb0344e6cac211ab1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="92c0a-102">COR_ARRAY_LAYOUT — Struktury</span><span class="sxs-lookup"><span data-stu-id="92c0a-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="92c0a-103">Zawiera informacje o układzie tablicy obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="92c0a-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92c0a-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="92c0a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="92c0a-105">Members</span></span>  
  
|<span data-ttu-id="92c0a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="92c0a-106">Member</span></span>|<span data-ttu-id="92c0a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="92c0a-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="92c0a-108">Identyfikator typu obiektów zawartych w tablicy.</span><span class="sxs-lookup"><span data-stu-id="92c0a-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="92c0a-109">Wartość wyliczenia CorElementType, która wskazuje, czy składnik jest odwołanie do kolekcji odzyskiwanie, klasą wartości lub typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="92c0a-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="92c0a-110">Przesunięcie do pierwszego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="92c0a-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="92c0a-111">Rozmiar każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="92c0a-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="92c0a-112">Przesunięcie do liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="92c0a-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="92c0a-113">Rozmiar w bajtach stopnia.</span><span class="sxs-lookup"><span data-stu-id="92c0a-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="92c0a-114">Liczba rangi tablicy.</span><span class="sxs-lookup"><span data-stu-id="92c0a-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="92c0a-115">Przesunięcie, jaką start rangę.</span><span class="sxs-lookup"><span data-stu-id="92c0a-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92c0a-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92c0a-116">Remarks</span></span>  
 <span data-ttu-id="92c0a-117">`rankSize` Pole określa rozmiar pozycji w tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="92c0a-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="92c0a-118">Jest dokładne dla również tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="92c0a-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="92c0a-119">Wartość `numRanks` 1 dla tablicy jednowymiarowej i `N` dla tablicy wielowymiarowej z `N` wymiarów.</span><span class="sxs-lookup"><span data-stu-id="92c0a-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c0a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92c0a-120">Requirements</span></span>  
 <span data-ttu-id="92c0a-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c0a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c0a-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92c0a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92c0a-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92c0a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c0a-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c0a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c0a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92c0a-125">See Also</span></span>  
 [<span data-ttu-id="92c0a-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="92c0a-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="92c0a-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="92c0a-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
