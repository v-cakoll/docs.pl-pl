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
ms.openlocfilehash: 2b01acbd617b13a64ef3dca6c8661f1e6bb067ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447386"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="ae32f-102">COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="ae32f-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="ae32f-103">Reprezentuje argumenty funkcji w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="ae32f-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae32f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae32f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ae32f-105">Members</span><span class="sxs-lookup"><span data-stu-id="ae32f-105">Members</span></span>  
  
|<span data-ttu-id="ae32f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ae32f-106">Member</span></span>|<span data-ttu-id="ae32f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ae32f-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="ae32f-108">Liczba bloków argumentów.</span><span class="sxs-lookup"><span data-stu-id="ae32f-108">The number of blocks of arguments.</span></span> <span data-ttu-id="ae32f-109">Oznacza to, że ta wartość jest liczbą struktur [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) w tablicy `ranges`.</span><span class="sxs-lookup"><span data-stu-id="ae32f-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="ae32f-110">Łączny rozmiar wszystkich argumentów.</span><span class="sxs-lookup"><span data-stu-id="ae32f-110">The total size of all arguments.</span></span> <span data-ttu-id="ae32f-111">Innymi słowy, ta wartość jest sumą argumentów długości.</span><span class="sxs-lookup"><span data-stu-id="ae32f-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="ae32f-112">Tablica struktur `COR_PRF_FUNCTION_ARGUMENT_RANGE`, z których każdy reprezentuje jeden blok argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae32f-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae32f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae32f-113">Remarks</span></span>  
 <span data-ttu-id="ae32f-114">Funkcja może mieć wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="ae32f-114">A function may have many arguments.</span></span> <span data-ttu-id="ae32f-115">Te argumenty mogą nie być przechowywane w sposób ciągły w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ae32f-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="ae32f-116">Może istnieć blok trzech argumentów w jednym miejscu, blok dwóch argumentów w innym miejscu i końcowy blok jednego argumentu w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="ae32f-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="ae32f-117">Te argumenty są wszystkie dla tej samej funkcji; są one po prostu przechowywane w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="ae32f-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="ae32f-118">Struktura `COR_PRF_FUNCTION_ARGUMENT_INFO` reprezentuje wszystkie argumenty pojedynczej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae32f-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="ae32f-119">Używa tablicy do odwoływania się do wszystkich bloków argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae32f-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="ae32f-120">Dlatego w przypadku pojedynczej funkcji istnieje jedna struktura `COR_PRF_FUNCTION_ARGUMENT_INFO`, która odwołuje się do wielu struktur `COR_PRF_FUNCTION_ARGUMENT_RANGE`, z których każdy wskazuje jeden lub więcej argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae32f-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="ae32f-121">Argumenty, które są przechowywane w rejestrach, są rozlane do pamięci, aby kompilować struktury.</span><span class="sxs-lookup"><span data-stu-id="ae32f-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae32f-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae32f-122">Requirements</span></span>  
 <span data-ttu-id="ae32f-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae32f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae32f-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="ae32f-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ae32f-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ae32f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae32f-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae32f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae32f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae32f-127">See also</span></span>

- [<span data-ttu-id="ae32f-128">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="ae32f-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
