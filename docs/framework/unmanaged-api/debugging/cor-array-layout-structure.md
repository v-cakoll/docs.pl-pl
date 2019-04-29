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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609571"
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="4e980-102">COR_ARRAY_LAYOUT — Struktury</span><span class="sxs-lookup"><span data-stu-id="4e980-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="4e980-103">Informacje dotyczące układu obiektu tablicowego w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4e980-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e980-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e980-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4e980-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4e980-105">Members</span></span>  
  
|<span data-ttu-id="4e980-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4e980-106">Member</span></span>|<span data-ttu-id="4e980-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4e980-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="4e980-108">Identyfikator typu obiektów zawartych w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4e980-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="4e980-109">Corelementtype — wartość wyliczenia, która wskazuje, czy składnik jest odwołanie do kolekcji wyrzucania elementów, klasą wartości lub elementu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4e980-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="4e980-110">Przesunięcie do pierwszego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4e980-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="4e980-111">Rozmiar każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="4e980-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="4e980-112">Przesunięcie do liczby elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4e980-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="4e980-113">Rozmiar w bajtach rangi.</span><span class="sxs-lookup"><span data-stu-id="4e980-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="4e980-114">Liczba rangę tablicy.</span><span class="sxs-lookup"><span data-stu-id="4e980-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="4e980-115">Przesunięcie, w którym start rangę.</span><span class="sxs-lookup"><span data-stu-id="4e980-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e980-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e980-116">Remarks</span></span>  
 <span data-ttu-id="4e980-117">`rankSize` Pola określa rozmiar rangę tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="4e980-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="4e980-118">Jest prawidłowe dla także tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="4e980-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="4e980-119">Wartość `numRanks` 1 dla tablicy jednowymiarowej i `N` dla tablicy wielowymiarowej `N` wymiarów.</span><span class="sxs-lookup"><span data-stu-id="4e980-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e980-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e980-120">Requirements</span></span>  
 <span data-ttu-id="4e980-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e980-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e980-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e980-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e980-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e980-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e980-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e980-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e980-125">See also</span></span>

- [<span data-ttu-id="4e980-126">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="4e980-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4e980-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4e980-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
