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
ms.openlocfilehash: 4cfacb7f3303947ec8b11362fde82649687889d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792666"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="f9ba1-102">ICorDebugProcess::ClearCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9ba1-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="f9ba1-103">Czyści bieżący wyjątek niezarządzany w danym wątku.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ba1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9ba1-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9ba1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9ba1-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="f9ba1-106">podczas Identyfikator wątku, w którym zostanie wyczyszczony bieżący wyjątek niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9ba1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9ba1-107">Remarks</span></span>  
 <span data-ttu-id="f9ba1-108">Wywołaj tę metodę przed wywołaniem [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , gdy wątek zgłosił wyjątek niezarządzany, który powinien zostać zignorowany przez debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="f9ba1-109">Spowoduje to wyczyszczenie wszystkich oczekujących zdarzeń w paśmie (IB) i poza pasmem (OOB) w danym wątku.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="f9ba1-110">Wszystkie punkty przerwania OOB i wyjątki pojedynczego kroku są automatycznie wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="f9ba1-111">Użyj [ICorDebugThread2:: InterceptCurrentException —](icordebugthread2-interceptcurrentexception-method.md) , aby przechwycić bieżący wyjątek zarządzany wątku.</span><span class="sxs-lookup"><span data-stu-id="f9ba1-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ba1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9ba1-112">Requirements</span></span>  
 <span data-ttu-id="f9ba1-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9ba1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ba1-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9ba1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9ba1-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f9ba1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9ba1-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ba1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
