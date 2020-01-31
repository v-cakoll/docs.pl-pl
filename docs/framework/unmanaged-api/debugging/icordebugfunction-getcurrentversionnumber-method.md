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
ms.openlocfilehash: 5e080e9aa89816b24aa2eb1b6b1be823922e86fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794518"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="1d5bc-102">ICorDebugFunction::GetCurrentVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d5bc-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="1d5bc-103">Pobiera numer wersji najnowszej edycji wykonanej do funkcji reprezentowanej przez ten obiekt ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="1d5bc-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d5bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d5bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d5bc-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="1d5bc-106">określoną Wskaźnik do wartości całkowitej, która jest numerem wersji najnowszej edycji wykonanej w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1d5bc-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d5bc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d5bc-107">Remarks</span></span>  
 <span data-ttu-id="1d5bc-108">Numer wersji najnowszej edycji tej funkcji może być większy niż numer wersji samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1d5bc-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="1d5bc-109">Użyj metody [ICorDebugFunction2:: GetVersionNumber —](icordebugfunction2-getversionnumber-method.md) lub [ICorDebugCode:: GetVersionNumber —](icordebugcode-getversionnumber-method.md) do pobrania numeru wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="1d5bc-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d5bc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d5bc-110">Requirements</span></span>  
 <span data-ttu-id="1d5bc-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d5bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d5bc-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d5bc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d5bc-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1d5bc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d5bc-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d5bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
