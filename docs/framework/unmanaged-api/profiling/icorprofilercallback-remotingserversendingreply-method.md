---
title: "ICorProfilerCallback::RemotingServerSendingReply — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b99b2de235634b715a6f5ba9fee9ee49ab34063a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="3acdf-102">ICorProfilerCallback::RemotingServerSendingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="3acdf-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="3acdf-103">Powiadamia profilera, że proces zakończył przetwarzanie żądania wywołania metody zdalnego i ma przesyłać odpowiedzi za pośrednictwem kanału.</span><span class="sxs-lookup"><span data-stu-id="3acdf-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3acdf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3acdf-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3acdf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3acdf-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="3acdf-106">[in] Wskaźnik identyfikator GUID, który będzie odpowiadać wartości podanej w [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="3acdf-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="3acdf-107">Pliki cookie GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="3acdf-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="3acdf-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="3acdf-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="3acdf-109">Identyfikator GUID pliki cookie są aktywne w procesie po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="3acdf-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="3acdf-110">Umożliwia łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logiczne.</span><span class="sxs-lookup"><span data-stu-id="3acdf-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="3acdf-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3acdf-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3acdf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3acdf-112">Requirements</span></span>  
 <span data-ttu-id="3acdf-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3acdf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3acdf-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3acdf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3acdf-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3acdf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3acdf-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3acdf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acdf-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3acdf-117">See Also</span></span>  
 [<span data-ttu-id="3acdf-118">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="3acdf-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
