---
title: ICorDebugFunction::GetCurrentVersionNumber — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 0530ba742a739003bfa33079ad75cb1e6f5f5e59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124017"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="b569d-102">ICorDebugFunction::GetCurrentVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="b569d-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="b569d-103">Pobiera numer wersji najnowszej edycji wykonanej do funkcji reprezentowanej przez ten obiekt ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="b569d-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b569d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b569d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b569d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b569d-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="b569d-106">określoną Wskaźnik do wartości całkowitej, która jest numerem wersji najnowszej edycji wykonanej w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b569d-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b569d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b569d-107">Remarks</span></span>  
 <span data-ttu-id="b569d-108">Numer wersji najnowszej edycji tej funkcji może być większy niż numer wersji samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b569d-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="b569d-109">Użyj metody [ICorDebugFunction2:: GetVersionNumber —](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) lub [ICorDebugCode:: GetVersionNumber —](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) do pobrania numeru wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="b569d-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b569d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b569d-110">Requirements</span></span>  
 <span data-ttu-id="b569d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b569d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b569d-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b569d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b569d-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b569d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b569d-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b569d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
