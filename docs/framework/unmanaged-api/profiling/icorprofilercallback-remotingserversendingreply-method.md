---
title: ICorProfilerCallback::RemotingServerSendingReply — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6bf9f8241459f566eb0724596640fd6036ae799a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659621"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="ddfad-102">ICorProfilerCallback::RemotingServerSendingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddfad-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="ddfad-103">Powiadamia program profilujący, że proces zakończył przetwarzanie żądania wywołania zdalnej metody i ma przesłanie odpowiedzi za pośrednictwem kanału.</span><span class="sxs-lookup"><span data-stu-id="ddfad-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddfad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddfad-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddfad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddfad-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="ddfad-106">[in] Wskaźnik do identyfikatora GUID, które będą odpowiadać wartość podana w [icorprofilercallback::remotingclientreceivingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="ddfad-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="ddfad-107">Pliki cookie identyfikatora GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="ddfad-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="ddfad-108">Kanał powiedzie się podczas przesyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ddfad-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="ddfad-109">Identyfikator GUID pliki cookie są aktywne na proces po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="ddfad-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="ddfad-110">Dzięki temu można łatwo parowanie wywołaniem funkcji zdalnych wywołań i Tworzenie stosu wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="ddfad-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="ddfad-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ddfad-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddfad-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddfad-112">Requirements</span></span>  
 <span data-ttu-id="ddfad-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddfad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddfad-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddfad-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddfad-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddfad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddfad-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddfad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfad-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddfad-117">See also</span></span>
- [<span data-ttu-id="ddfad-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddfad-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
