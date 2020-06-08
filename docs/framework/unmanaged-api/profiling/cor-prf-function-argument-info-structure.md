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
ms.openlocfilehash: 9fca75ae59b95a226b51768b3e1bfb220d9926f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500967"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="6c977-102">COR_PRF_FUNCTION_ARGUMENT_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="6c977-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="6c977-103">Reprezentuje argumenty funkcji w kolejności od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="6c977-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c977-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c977-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="6c977-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6c977-105">Members</span></span>  
  
|<span data-ttu-id="6c977-106">Członek</span><span class="sxs-lookup"><span data-stu-id="6c977-106">Member</span></span>|<span data-ttu-id="6c977-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6c977-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="6c977-108">Liczba bloków argumentów.</span><span class="sxs-lookup"><span data-stu-id="6c977-108">The number of blocks of arguments.</span></span> <span data-ttu-id="6c977-109">Oznacza to, że ta wartość jest liczbą struktur [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) w `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6c977-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="6c977-110">Łączny rozmiar wszystkich argumentów.</span><span class="sxs-lookup"><span data-stu-id="6c977-110">The total size of all arguments.</span></span> <span data-ttu-id="6c977-111">Innymi słowy, ta wartość jest sumą argumentów długości.</span><span class="sxs-lookup"><span data-stu-id="6c977-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="6c977-112">Tablica `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktur, z których każdy reprezentuje jeden blok argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c977-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c977-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c977-113">Remarks</span></span>  
 <span data-ttu-id="6c977-114">Funkcja może mieć wiele argumentów.</span><span class="sxs-lookup"><span data-stu-id="6c977-114">A function may have many arguments.</span></span> <span data-ttu-id="6c977-115">Te argumenty mogą nie być przechowywane w sposób ciągły w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6c977-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="6c977-116">Może istnieć blok trzech argumentów w jednym miejscu, blok dwóch argumentów w innym miejscu i końcowy blok jednego argumentu w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="6c977-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="6c977-117">Te argumenty są wszystkie dla tej samej funkcji; są one po prostu przechowywane w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="6c977-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="6c977-118">`COR_PRF_FUNCTION_ARGUMENT_INFO`Struktura reprezentuje wszystkie argumenty pojedynczej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c977-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="6c977-119">Używa tablicy do odwoływania się do wszystkich bloków argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c977-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="6c977-120">Dlatego w przypadku pojedynczej funkcji masz jedną `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturę, która odwołuje `COR_PRF_FUNCTION_ARGUMENT_RANGE` się do wielu struktur, z których każdy wskazuje co najmniej jeden argument funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c977-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="6c977-121">Argumenty, które są przechowywane w rejestrach, są rozlane do pamięci, aby kompilować struktury.</span><span class="sxs-lookup"><span data-stu-id="6c977-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c977-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c977-122">Requirements</span></span>  
 <span data-ttu-id="6c977-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c977-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c977-124">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6c977-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6c977-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c977-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c977-126">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c977-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c977-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c977-127">See also</span></span>

- [<span data-ttu-id="6c977-128">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="6c977-128">Profiling Structures</span></span>](profiling-structures.md)
