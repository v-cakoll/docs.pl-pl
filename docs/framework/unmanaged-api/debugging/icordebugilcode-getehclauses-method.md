---
title: Metoda ICorDebugILCode::GetEHClauses
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d9ae1abc97d348dced9e4a21236c70658a9141
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488139"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="b8de6-102">Metoda ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="b8de6-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="b8de6-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b8de6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b8de6-104">Zwraca wskaźnik do listy wyjątków, obsługa klauzule (EH), które są zdefiniowane dla tego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="b8de6-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8de6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8de6-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8de6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8de6-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="b8de6-107">[in] Pojemność magazynu `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8de6-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b8de6-108">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b8de6-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="b8de6-109">[out] Liczba klauzul, o których informacje są zapisywane `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8de6-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="b8de6-110">Klauzule</span><span class="sxs-lookup"><span data-stu-id="b8de6-110">clauses</span></span>  
 <span data-ttu-id="b8de6-111">[out] Tablica [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) obiektów, które zawierają informacje dotyczące klauzul zdefiniowane dla tego IL obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b8de6-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8de6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8de6-112">Remarks</span></span>  
 <span data-ttu-id="b8de6-113">Jeśli `cClauses` wynosi 0 i `pcClauses` ma wartość inną niż**null**, `pcClauses` jest ustawiona na liczbę dostępnych obsługi klauzulach wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b8de6-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="b8de6-114">Jeśli `cClauses` jest różna od zera, reprezentuje pojemność magazynu `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8de6-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b8de6-115">Po powrocie z metody `clauses` może zawierać maksymalnie `cClauses` elementów, a `pcClauses` jest ustawienie liczby klauzul rzeczywiście zapisanych na `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b8de6-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8de6-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8de6-116">Requirements</span></span>  
 <span data-ttu-id="b8de6-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8de6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8de6-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8de6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8de6-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8de6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8de6-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8de6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8de6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8de6-121">See also</span></span>
- [<span data-ttu-id="b8de6-122">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8de6-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="b8de6-123">CorDebugEHClause, struktura</span><span class="sxs-lookup"><span data-stu-id="b8de6-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="b8de6-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b8de6-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
