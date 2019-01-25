---
title: ICorProfilerCallback::RemotingClientSendingMessage — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 424e0323c018367560d4cf3542e9e8668575a03f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675240"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="83d57-102">ICorProfilerCallback::RemotingClientSendingMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="83d57-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="83d57-103">Powiadamia program profilujący, że klient wysyła żądanie do serwera.</span><span class="sxs-lookup"><span data-stu-id="83d57-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d57-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83d57-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83d57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83d57-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="83d57-106">[in] Wartość, która odpowiada za pomocą wartość podana w [icorprofilercallback::remotingserverreceivingmessage —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="83d57-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="83d57-107">Pliki cookie identyfikatora GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="83d57-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="83d57-108">Kanał powiedzie się podczas przesyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="83d57-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="83d57-109">Identyfikator GUID pliki cookie są aktywne na proces po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="83d57-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="83d57-110">Dzięki temu można łatwo parowanie wywołaniem funkcji zdalnych wywołań i Tworzenie stosu wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="83d57-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="83d57-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="83d57-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d57-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83d57-112">Requirements</span></span>  
 <span data-ttu-id="83d57-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d57-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d57-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83d57-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83d57-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83d57-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83d57-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d57-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d57-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83d57-117">See also</span></span>
- [<span data-ttu-id="83d57-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="83d57-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
