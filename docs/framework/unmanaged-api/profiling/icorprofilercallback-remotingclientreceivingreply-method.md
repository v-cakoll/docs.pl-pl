---
title: ICorProfilerCallback::RemotingClientReceivingReply — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2134a7f12ac482b3fe79ac722684ac8601a7280b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662923"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="cbb8d-102">ICorProfilerCallback::RemotingClientReceivingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbb8d-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="cbb8d-103">Powiadamia program profilujący po stronie serwera część wywołanie komunikacji zdalnej została zakończona i klient otrzymuje teraz i wkrótce do przetwarzania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbb8d-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="cbb8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbb8d-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="cbb8d-106">[in] Wartość, która będzie odpowiadać za pomocą wartość podana w [icorprofilercallback::remotingserversendingreply —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="cbb8d-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="cbb8d-107">Pliki cookie identyfikatora GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="cbb8d-108">Kanał powiedzie się podczas przesyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="cbb8d-109">Identyfikator GUID pliki cookie są aktywne na proces po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="cbb8d-110">Dzięki temu można łatwo parowanie wywołaniem funkcji zdalnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="cbb8d-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbb8d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbb8d-112">Requirements</span></span>  
 <span data-ttu-id="cbb8d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb8d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb8d-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbb8d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbb8d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbb8d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbb8d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb8d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb8d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbb8d-117">See also</span></span>

- [<span data-ttu-id="cbb8d-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbb8d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
