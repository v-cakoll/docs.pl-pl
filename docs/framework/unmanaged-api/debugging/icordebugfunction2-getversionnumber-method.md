---
title: ICorDebugFunction2::GetVersionNumber — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420056"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="d39d1-102">ICorDebugFunction2::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="d39d1-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="d39d1-103">Pobiera wersję tej funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="d39d1-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d39d1-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d39d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d39d1-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="d39d1-106">[out] Wskaźnik do wartości całkowitej, numer wersji reprezentowanego przez ten obiekt ICorDebugFunction2 funkcji.</span><span class="sxs-lookup"><span data-stu-id="d39d1-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d39d1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d39d1-107">Remarks</span></span>  
 <span data-ttu-id="d39d1-108">Środowisko uruchomieniowe przechowuje informacje o liczbę zmian, które miały miejsce do poszczególnych modułów podczas sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="d39d1-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="d39d1-109">Numer wersji funkcji jest jednym więcej niż liczba edycji, który wprowadzono funkcję.</span><span class="sxs-lookup"><span data-stu-id="d39d1-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="d39d1-110">Funkcja oryginalnej wersji jest w wersji 1.</span><span class="sxs-lookup"><span data-stu-id="d39d1-110">The function's original version is version 1.</span></span> <span data-ttu-id="d39d1-111">Numer jest zwiększany modułu zawsze [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) zostanie wywołany dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="d39d1-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="d39d1-112">W związku z tym jeśli treść funkcji został zastąpiony w wywołaniu pierwszy i trzeci `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` może zwrócić w wersji 1, 2 lub 4 dla tej funkcji, ale nie w wersji 3.</span><span class="sxs-lookup"><span data-stu-id="d39d1-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="d39d1-113">(Ta funkcja będzie miała nie w wersji 3.)</span><span class="sxs-lookup"><span data-stu-id="d39d1-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="d39d1-114">Numer wersji jest osobno dla każdego modułu.</span><span class="sxs-lookup"><span data-stu-id="d39d1-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="d39d1-115">Tak po wykonaniu czterech zmiany w Module 1 i żaden moduł 2 dalej edycji w Module 1 przypisze numer wersji 6 wszystkie funkcje edycji w Module 1.</span><span class="sxs-lookup"><span data-stu-id="d39d1-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="d39d1-116">Jeśli takie same edytować poprawki modułu 2, funkcji w Module 2 otrzyma numer wersji 2.</span><span class="sxs-lookup"><span data-stu-id="d39d1-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="d39d1-117">Numer wersji uzyskany przez `GetVersionNumber` metoda może być mniejszy niż uzyskany przez [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="d39d1-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="d39d1-118">[ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda wykonuje tę samą operację jako `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="d39d1-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d39d1-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d39d1-119">Requirements</span></span>  
 <span data-ttu-id="d39d1-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d39d1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d39d1-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d39d1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d39d1-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d39d1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d39d1-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d39d1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
