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
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497174"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="a7a4c-102">ICorDebugFunction2::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7a4c-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="a7a4c-103">Pobiera Edytuj i Kontynuuj wersja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a4c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7a4c-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7a4c-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="a7a4c-106">[out] Wskaźnik do liczby całkowitej, który jest numer wersji funkcji, który jest reprezentowany przez ten obiekt icordebugfunction2 —.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7a4c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7a4c-107">Remarks</span></span>  
 <span data-ttu-id="a7a4c-108">Środowisko uruchomieniowe przechowuje informacje o liczbę zmian, które miały miejsce do poszczególnych modułów podczas sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="a7a4c-109">Numer wersji funkcji jest jednym więcej niż liczba edycji, który wprowadzono funkcję.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="a7a4c-110">Oryginalna wersja funkcji jest w wersji 1.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-110">The function's original version is version 1.</span></span> <span data-ttu-id="a7a4c-111">Numer jest zwiększany dla modułu, każdym razem, gdy [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) jest wywoływana w module.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="a7a4c-112">W związku z tym jeśli treść funkcji został zastąpiony w wywołaniu pierwszy i trzeci `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` może zwrócić wersję 1, 2 lub 4 dla tej funkcji, ale nie w wersji 3.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="a7a4c-113">(Ta funkcja będzie miała wersji 3).</span><span class="sxs-lookup"><span data-stu-id="a7a4c-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="a7a4c-114">Numer wersji jest śledzone oddzielnie dla każdego modułu.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="a7a4c-115">Tak Jeśli cztery edycje na Module 1 i brak na Module 2, dalej zmiany w Module 1 przypisze numeru wersji 6 wszystkie funkcje edytowanych w Module 1.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="a7a4c-116">Jeśli moduł 2 ma takie same edytować, funkcje w Module 2 zostanie wyświetlony numer wersji 2.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="a7a4c-117">Numer wersji uzyskanych przez `GetVersionNumber` metoda może być mniejszy niż uzyskanych przez [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="a7a4c-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="a7a4c-118">[ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda wykonuje tej samej operacji co `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="a7a4c-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a4c-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7a4c-119">Requirements</span></span>  
 <span data-ttu-id="a7a4c-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a4c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a4c-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7a4c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7a4c-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7a4c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7a4c-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a4c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
