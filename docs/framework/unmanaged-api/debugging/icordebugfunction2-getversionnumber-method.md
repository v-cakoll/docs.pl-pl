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
ms.openlocfilehash: 5826297d8151cf05e1ec08acbf5c9cd381d2452b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137808"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="ffa05-102">ICorDebugFunction2::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="ffa05-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="ffa05-103">Pobiera wersję Edytuj i Kontynuuj tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ffa05-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa05-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffa05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffa05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffa05-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="ffa05-106">określoną Wskaźnik do liczby całkowitej, która jest numerem wersji funkcji reprezentowanej przez ten obiekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="ffa05-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffa05-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffa05-107">Remarks</span></span>  
 <span data-ttu-id="ffa05-108">Środowisko uruchomieniowe śledzi liczbę zmian, które zostały zastosowane do każdego modułu podczas sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="ffa05-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="ffa05-109">Numer wersji funkcji jest jeden więcej niż liczba edycji, która wprowadziła funkcję.</span><span class="sxs-lookup"><span data-stu-id="ffa05-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="ffa05-110">Oryginalna wersja funkcji to wersja 1.</span><span class="sxs-lookup"><span data-stu-id="ffa05-110">The function's original version is version 1.</span></span> <span data-ttu-id="ffa05-111">Liczba jest zwiększana dla modułu za każdym razem, gdy [ICorDebugModule2:: ApplyChanges —](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) jest wywoływana dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="ffa05-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="ffa05-112">Tak więc, jeśli treść funkcji została zastąpiona w pierwszym i trzecim wywołaniu `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` może zwrócić wersję 1, 2 lub 4 dla tej funkcji, ale nie w wersji 3.</span><span class="sxs-lookup"><span data-stu-id="ffa05-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="ffa05-113">(Ta funkcja nie ma wersji 3).</span><span class="sxs-lookup"><span data-stu-id="ffa05-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="ffa05-114">Numer wersji jest śledzony oddzielnie dla każdego modułu.</span><span class="sxs-lookup"><span data-stu-id="ffa05-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="ffa05-115">Dlatego w przypadku przeprowadzenia czterech zmian w module 1 i braku w module 2 kolejna edycja w module 1 przypisze numer wersji 6 do wszystkich edytowanych funkcji w module 1.</span><span class="sxs-lookup"><span data-stu-id="ffa05-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="ffa05-116">Jeśli ta sama Edycja obejmuje moduł 2, funkcje w module 2 uzyskają numer wersji 2.</span><span class="sxs-lookup"><span data-stu-id="ffa05-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="ffa05-117">Numer wersji uzyskany przez metodę `GetVersionNumber` może być niższy niż uzyskany przez [ICorDebugFunction:: GetCurrentVersionNumber —](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="ffa05-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="ffa05-118">Metoda [ICorDebugCode:: GetVersionNumber —](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) wykonuje tę samą operację co `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="ffa05-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa05-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffa05-119">Requirements</span></span>  
 <span data-ttu-id="ffa05-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa05-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa05-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ffa05-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffa05-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ffa05-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffa05-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa05-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
