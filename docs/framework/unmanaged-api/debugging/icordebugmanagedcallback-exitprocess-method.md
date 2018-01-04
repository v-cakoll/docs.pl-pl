---
title: "ICorDebugManagedCallback::ExitProcess — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7be74520fff65b113f54d82305a84dd183286876
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="c0398-102">ICorDebugManagedCallback::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0398-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="c0398-103">Powiadamia debugera, że proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="c0398-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0398-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0398-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0398-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0398-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="c0398-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje procesu.</span><span class="sxs-lookup"><span data-stu-id="c0398-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0398-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0398-107">Remarks</span></span>  
 <span data-ttu-id="c0398-108">Nie można kontynuować z `ExitProcess` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c0398-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="c0398-109">To zdarzenie może wyzwalać asynchronicznie z innymi zdarzeniami podczas procesu wydaje się być zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="c0398-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="c0398-110">Może to wystąpić, jeśli proces zakończy się podczas zatrzymana, zazwyczaj z powodu niektóre siły zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="c0398-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="c0398-111">Jeśli środowisko uruchomieniowe języka wspólnego (CLR) wysyła już zarządzane wywołania zwrotnego, to zdarzenie zostanie opóźnione aż do po zwrócił wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="c0398-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="c0398-112">`ExitProcess` Zdarzenie jest tylko zdarzenia zakończenia i zwalniania, które może być wywoływana w zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="c0398-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0398-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0398-113">Requirements</span></span>  
 <span data-ttu-id="c0398-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0398-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0398-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0398-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0398-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0398-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0398-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0398-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0398-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0398-118">See Also</span></span>  
 [<span data-ttu-id="c0398-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0398-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
