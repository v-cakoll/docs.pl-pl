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
ms.openlocfilehash: ac9a4e4b54b302afeae4ede1dd574c15ded3ff12
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788601"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="b6c46-102">Metoda ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="b6c46-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="b6c46-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b6c46-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b6c46-104">Zwraca wskaźnik do listy klauzul obsługi wyjątków (EH), które są zdefiniowane dla tego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="b6c46-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c46-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6c46-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6c46-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6c46-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="b6c46-107">podczas Pojemność magazynu tablicy `clauses`.</span><span class="sxs-lookup"><span data-stu-id="b6c46-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b6c46-108">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b6c46-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="b6c46-109">określoną Liczba klauzul, na których informacje są zapisywane w tablicy `clauses`.</span><span class="sxs-lookup"><span data-stu-id="b6c46-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="b6c46-110">warunki</span><span class="sxs-lookup"><span data-stu-id="b6c46-110">clauses</span></span>  
 <span data-ttu-id="b6c46-111">określoną Tablica obiektów [CorDebugEHClause](cordebugehclause-structure.md) , które zawierają informacje na temat klauzul obsługi wyjątków zdefiniowane dla tego Il.</span><span class="sxs-lookup"><span data-stu-id="b6c46-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6c46-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6c46-112">Remarks</span></span>  
 <span data-ttu-id="b6c46-113">Jeśli `cClauses` ma wartość 0, a `pcClauses` ma**wartość**różną od null, `pcClauses` jest ustawiona na liczbę dostępnych klauzul obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b6c46-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="b6c46-114">Jeśli `cClauses` jest różna od zera, reprezentuje pojemność magazynu `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b6c46-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b6c46-115">Gdy metoda zwraca, `clauses` zawiera maksymalnie `cClauses` elementów, a `pcClauses` jest ustawiona na liczbę klauzul, które faktycznie Zapisano do tablicy `clauses`.</span><span class="sxs-lookup"><span data-stu-id="b6c46-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c46-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6c46-116">Requirements</span></span>  
 <span data-ttu-id="b6c46-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6c46-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c46-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6c46-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6c46-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6c46-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6c46-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c46-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c46-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6c46-121">See also</span></span>

- [<span data-ttu-id="b6c46-122">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6c46-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="b6c46-123">CorDebugEHClause, struktura</span><span class="sxs-lookup"><span data-stu-id="b6c46-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="b6c46-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6c46-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
