---
title: ICorProfilerCallback::RemotingServerReceivingMessage — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1874b5bea465eb31bcaad2d912b90d35cfc711b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454111"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="75ce4-102">ICorProfilerCallback::RemotingServerReceivingMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="75ce4-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="75ce4-103">Powiadamia profilera, że proces odebrał żądanie aktywacji lub wywołanie metody zdalnego.</span><span class="sxs-lookup"><span data-stu-id="75ce4-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ce4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75ce4-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75ce4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75ce4-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="75ce4-106">[in] Wartość, która będzie zgodne z wartością w [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="75ce4-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="75ce4-107">Pliki cookie GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="75ce4-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="75ce4-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="75ce4-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="75ce4-109">Identyfikator GUID pliki cookie są aktywne w procesie po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="75ce4-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="75ce4-110">Umożliwia łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logiczne.</span><span class="sxs-lookup"><span data-stu-id="75ce4-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="75ce4-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="75ce4-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75ce4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75ce4-112">Remarks</span></span>  
 <span data-ttu-id="75ce4-113">Jeśli żądanie komunikatu jest asynchroniczny, żądanie może być obsługiwany przez wszystkie wątki dowolnego.</span><span class="sxs-lookup"><span data-stu-id="75ce4-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ce4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75ce4-114">Requirements</span></span>  
 <span data-ttu-id="75ce4-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75ce4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75ce4-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75ce4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75ce4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75ce4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75ce4-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75ce4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ce4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75ce4-119">See Also</span></span>  
 [<span data-ttu-id="75ce4-120">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="75ce4-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
