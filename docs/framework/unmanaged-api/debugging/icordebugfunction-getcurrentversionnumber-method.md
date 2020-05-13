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
ms.openlocfilehash: b47580022b98ea02584a94b3f74b3fd1c276f297
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212909"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="69d6a-102">ICorDebugFunction::GetCurrentVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="69d6a-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="69d6a-103">Pobiera numer wersji najnowszej edycji wykonanej do funkcji reprezentowanej przez ten obiekt ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="69d6a-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69d6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69d6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69d6a-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="69d6a-106">określoną Wskaźnik do wartości całkowitej, która jest numerem wersji najnowszej edycji wykonanej w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="69d6a-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69d6a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69d6a-107">Remarks</span></span>  
 <span data-ttu-id="69d6a-108">Numer wersji najnowszej edycji tej funkcji może być większy niż numer wersji samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="69d6a-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="69d6a-109">Użyj metody [ICorDebugFunction2:: GetVersionNumber —](icordebugfunction2-getversionnumber-method.md) lub [ICorDebugCode:: GetVersionNumber —](icordebugcode-getversionnumber-method.md) do pobrania numeru wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="69d6a-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69d6a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69d6a-110">Requirements</span></span>  
 <span data-ttu-id="69d6a-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69d6a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69d6a-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69d6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69d6a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69d6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69d6a-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69d6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
