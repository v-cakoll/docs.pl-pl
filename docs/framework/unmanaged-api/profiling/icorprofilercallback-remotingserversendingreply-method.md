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
ms.openlocfilehash: 98563c175f12ad1ff25e1f578270fe1099175487
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453779"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="c6add-102">ICorProfilerCallback::RemotingServerSendingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6add-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="c6add-103">Powiadamia profilera, że proces zakończył przetwarzanie żądania wywołania metody zdalnego i ma przesyłać odpowiedzi za pośrednictwem kanału.</span><span class="sxs-lookup"><span data-stu-id="c6add-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6add-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6add-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6add-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6add-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="c6add-106">[in] Wskaźnik identyfikator GUID, który będzie odpowiadać wartości podanej w [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="c6add-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="c6add-107">Pliki cookie GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="c6add-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="c6add-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="c6add-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="c6add-109">Identyfikator GUID pliki cookie są aktywne w procesie po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="c6add-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="c6add-110">Umożliwia łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logiczne.</span><span class="sxs-lookup"><span data-stu-id="c6add-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="c6add-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c6add-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6add-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6add-112">Requirements</span></span>  
 <span data-ttu-id="c6add-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6add-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6add-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6add-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6add-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6add-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6add-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6add-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6add-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6add-117">See Also</span></span>  
 [<span data-ttu-id="c6add-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6add-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
