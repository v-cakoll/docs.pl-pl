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
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210387"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="77d10-102">Metoda ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="77d10-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="77d10-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="77d10-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="77d10-104">Zwraca wskaźnik do listy klauzul obsługi wyjątków (EH), które są zdefiniowane dla tego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="77d10-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="77d10-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77d10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="77d10-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="77d10-107">podczas Pojemność magazynu `clauses` macierzy.</span><span class="sxs-lookup"><span data-stu-id="77d10-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="77d10-108">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="77d10-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="77d10-109">określoną Liczba klauzul, na których informacje są zapisywane w `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="77d10-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="77d10-110">warunki</span><span class="sxs-lookup"><span data-stu-id="77d10-110">clauses</span></span>  
 <span data-ttu-id="77d10-111">określoną Tablica obiektów [CorDebugEHClause](cordebugehclause-structure.md) , które zawierają informacje na temat klauzul obsługi wyjątków zdefiniowane dla tego Il.</span><span class="sxs-lookup"><span data-stu-id="77d10-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d10-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77d10-112">Remarks</span></span>  
 <span data-ttu-id="77d10-113">Jeśli wartość `cClauses` jest równa 0 i `pcClauses` ma wartość różną od**null**, `pcClauses` jest ustawiona na liczbę dostępnych klauzul obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="77d10-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="77d10-114">Jeśli `cClauses` jest różna od zera, reprezentuje pojemność magazynu `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="77d10-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="77d10-115">Gdy metoda zwraca, `clauses` zawiera maksimum `cClauses` elementów i `pcClauses` jest ustawiona na liczbę klauzul faktycznie zapisywana w `clauses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="77d10-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d10-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77d10-116">Requirements</span></span>  
 <span data-ttu-id="77d10-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d10-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d10-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="77d10-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77d10-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="77d10-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77d10-120">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d10-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d10-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77d10-121">See also</span></span>

- [<span data-ttu-id="77d10-122">Interfejs ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="77d10-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="77d10-123">Struktura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="77d10-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="77d10-124">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="77d10-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
