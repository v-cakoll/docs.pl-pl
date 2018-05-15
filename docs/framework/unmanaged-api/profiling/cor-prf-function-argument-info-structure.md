---
title: COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fbc41ca1366b412c37d6af09e90e3f1b042ba21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="13e7a-102">COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="13e7a-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="13e7a-103">Reprezentuje argumenty funkcji w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="13e7a-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13e7a-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="13e7a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="13e7a-105">Members</span></span>  
  
|<span data-ttu-id="13e7a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="13e7a-106">Member</span></span>|<span data-ttu-id="13e7a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="13e7a-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="13e7a-108">Liczba bloków argumentów.</span><span class="sxs-lookup"><span data-stu-id="13e7a-108">The number of blocks of arguments.</span></span> <span data-ttu-id="13e7a-109">Oznacza to, że ta wartość jest liczbą [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktury w `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="13e7a-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="13e7a-110">Całkowity rozmiar wszystkich argumentów.</span><span class="sxs-lookup"><span data-stu-id="13e7a-110">The total size of all arguments.</span></span> <span data-ttu-id="13e7a-111">Innymi słowy ta wartość jest suma długości argumentu.</span><span class="sxs-lookup"><span data-stu-id="13e7a-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="13e7a-112">Tablica `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z których każdy reprezentuje jeden blok argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="13e7a-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13e7a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13e7a-113">Remarks</span></span>  
 <span data-ttu-id="13e7a-114">Funkcja może mieć wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="13e7a-114">A function may have many arguments.</span></span> <span data-ttu-id="13e7a-115">Tych argumentów nie może być połączone ze sobą przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="13e7a-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="13e7a-116">Może być blokiem trzech argumentów w jednym miejscu, blok dwa argumenty w innym miejscu i bloku końcowego jeden argument w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="13e7a-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="13e7a-117">Wyświetlane są wszystkie argumenty dla tej samej funkcji; po prostu są one przechowywane w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="13e7a-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="13e7a-118">`COR_PRF_FUNCTION_ARGUMENT_INFO` Struktury reprezentuje wszystkie argumenty funkcji pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="13e7a-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="13e7a-119">Aby odwołać wszystkie bloki argumentów funkcji używa tablicy.</span><span class="sxs-lookup"><span data-stu-id="13e7a-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="13e7a-120">Tak, dla jednej funkcji, należy mieć pojedynczy `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury, która odwołuje się do wielu `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z których każdy wskazuje co najmniej jeden z argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="13e7a-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="13e7a-121">Argumenty, które są przechowywane w rejestrach są rozrzucone w pamięci, aby skompilować struktur.</span><span class="sxs-lookup"><span data-stu-id="13e7a-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e7a-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13e7a-122">Requirements</span></span>  
 <span data-ttu-id="13e7a-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e7a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e7a-124">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="13e7a-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="13e7a-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13e7a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13e7a-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e7a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e7a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13e7a-127">See Also</span></span>  
 [<span data-ttu-id="13e7a-128">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="13e7a-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
