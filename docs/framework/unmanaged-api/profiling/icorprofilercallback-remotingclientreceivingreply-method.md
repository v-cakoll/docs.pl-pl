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
ms.openlocfilehash: 04956fb5519c66141f4bd7330367f6c78b4e7bc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453961"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="2ca18-102">ICorProfilerCallback::RemotingClientReceivingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ca18-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="2ca18-103">Powiadamia profiler Zakończono po stronie serwera część wywołaniem funkcji zdalnych i teraz odbiera klienta i informacje o przetwarzanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2ca18-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ca18-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ca18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ca18-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="2ca18-106">[in] Wartość, która będzie zgodne z wartością w [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="2ca18-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="2ca18-107">Pliki cookie GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="2ca18-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="2ca18-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="2ca18-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="2ca18-109">Identyfikator GUID pliki cookie są aktywne w procesie po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="2ca18-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="2ca18-110">Dzięki temu można łatwo parowanie zdalnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="2ca18-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="2ca18-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2ca18-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ca18-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ca18-112">Requirements</span></span>  
 <span data-ttu-id="2ca18-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ca18-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca18-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ca18-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ca18-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ca18-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ca18-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca18-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca18-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ca18-117">See Also</span></span>  
 [<span data-ttu-id="2ca18-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ca18-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
