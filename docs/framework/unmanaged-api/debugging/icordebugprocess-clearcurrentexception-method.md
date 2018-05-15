---
title: ICorDebugProcess::ClearCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2515e21ec00bd656eafd21a092a27304f7b1769
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="bba3f-102">ICorDebugProcess::ClearCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="bba3f-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="bba3f-103">Czyści niezarządzane bieżącego wyjątku dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="bba3f-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bba3f-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bba3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bba3f-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="bba3f-106">[in] Identyfikator wątku wyczyszczone bieżący wyjątek niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="bba3f-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bba3f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bba3f-107">Remarks</span></span>  
 <span data-ttu-id="bba3f-108">Wywołanie tej metody przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) po zgłosił niezarządzany wyjątek, który powinien być ignorowane przez obiekt debugowany wątek.</span><span class="sxs-lookup"><span data-stu-id="bba3f-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="bba3f-109">Spowoduje to wyczyszczenie zarówno oczekujących wewnątrzpasmowe (IB), jak i poza pasmem (OOB) zdarzenia dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="bba3f-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="bba3f-110">Wszystkie punkty przerwania OOB i pojedynczy krok wyjątki zostaną automatycznie wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="bba3f-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="bba3f-111">Użyj [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) przechwycenia bieżącego zarządzany wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="bba3f-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba3f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bba3f-112">Requirements</span></span>  
 <span data-ttu-id="bba3f-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba3f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba3f-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bba3f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bba3f-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bba3f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bba3f-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bba3f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
