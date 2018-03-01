---
title: Metoda ICorDebugILCode::GetEHClauses
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32b3a7bf7edaf15e44ea65e2d3b4f5037add8d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="94eae-102">Metoda ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="94eae-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="94eae-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="94eae-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="94eae-104">Zwraca wskaźnik do listy klauzule (EH), które są zdefiniowane dla tego języka pośrednim (IL) obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="94eae-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94eae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="94eae-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94eae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="94eae-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="94eae-107">[in] Pojemność `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="94eae-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="94eae-108">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="94eae-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="94eae-109">[out] Liczba klauzul, o których informacje są zapisywane w `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="94eae-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="94eae-110">klauzule</span><span class="sxs-lookup"><span data-stu-id="94eae-110">clauses</span></span>  
 <span data-ttu-id="94eae-111">[out] Tablica [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) obiektów, które zawierają informacje na temat zdefiniowane dla tego IL klauzule obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="94eae-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94eae-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94eae-112">Remarks</span></span>  
 <span data-ttu-id="94eae-113">Jeśli `cClauses` 0 i `pcClauses` ma wartość inną niż**null**, `pcClauses` wynosi liczba dostępnych klauzule obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="94eae-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="94eae-114">Jeśli `cClauses` jest różna od zera, reprezentuje pojemność `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="94eae-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="94eae-115">Gdy metoda zwróci wartość, `clauses` może zawierać maksymalnie `cClauses` elementów, i `pcClauses` ma ustawioną wartość liczba klauzul faktycznie zapisane `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="94eae-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94eae-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94eae-116">Requirements</span></span>  
 <span data-ttu-id="94eae-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94eae-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94eae-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94eae-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94eae-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94eae-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94eae-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94eae-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94eae-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94eae-121">See Also</span></span>  
 [<span data-ttu-id="94eae-122">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="94eae-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="94eae-123">CorDebugEHClause, struktura</span><span class="sxs-lookup"><span data-stu-id="94eae-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="94eae-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="94eae-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
