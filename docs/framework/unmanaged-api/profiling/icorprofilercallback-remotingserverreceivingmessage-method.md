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
ms.openlocfilehash: 30015cc6cae935c43cdbfec1a6eeae5c703ef9f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103210"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="3a77e-102">ICorProfilerCallback::RemotingServerReceivingMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a77e-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="3a77e-103">Powiadamia program profilujący, że proces odebrało żądanie aktywacji lub wywołanie metody zdalnej.</span><span class="sxs-lookup"><span data-stu-id="3a77e-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a77e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a77e-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a77e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a77e-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="3a77e-106">[in] Wartość, która będzie odpowiadać za pomocą wartość podana w [icorprofilercallback::remotingclientsendingmessage —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="3a77e-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="3a77e-107">Pliki cookie identyfikatora GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="3a77e-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="3a77e-108">Kanał powiedzie się podczas przesyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3a77e-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="3a77e-109">Identyfikator GUID pliki cookie są aktywne na proces po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="3a77e-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="3a77e-110">Dzięki temu można łatwo parowanie wywołaniem funkcji zdalnych wywołań i Tworzenie stosu wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="3a77e-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="3a77e-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3a77e-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a77e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a77e-112">Remarks</span></span>  
 <span data-ttu-id="3a77e-113">Jeśli żądanie komunikatu jest asynchroniczne, żądania mogą być obsługiwane w żadnym z dowolnych wątków.</span><span class="sxs-lookup"><span data-stu-id="3a77e-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a77e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a77e-114">Requirements</span></span>  
 <span data-ttu-id="3a77e-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a77e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a77e-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a77e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a77e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a77e-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3a77e-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3a77e-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3a77e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a77e-119">See also</span></span>

- [<span data-ttu-id="3a77e-120">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3a77e-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
