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
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175138"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="b38c9-102">ICorProfilerCallback::RemotingClientReceivingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="b38c9-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="b38c9-103">Powiadamia profiler, że część po stronie serwera wywołania komunikacji zdalnej została zakończona, a klient jest teraz odbieranie i zamierza przetworzyć odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b38c9-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b38c9-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="b38c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b38c9-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="b38c9-106">[w] Wartość, która będzie odpowiadać wartości podanej w [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="b38c9-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="b38c9-107">Aktywne są pliki cookie identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="b38c9-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="b38c9-108">Kanał udaje się przesłać wiadomość.</span><span class="sxs-lookup"><span data-stu-id="b38c9-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="b38c9-109">Pliki cookie guid są aktywne w procesie po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="b38c9-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="b38c9-110">Umożliwia to łatwe parowanie połączeń komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="b38c9-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="b38c9-111">[w] Wartość, która `true` jest, jeśli wywołanie jest asynchroniczne; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="b38c9-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b38c9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b38c9-112">Requirements</span></span>  
 <span data-ttu-id="b38c9-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b38c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38c9-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b38c9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b38c9-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b38c9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b38c9-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b38c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b38c9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b38c9-117">See also</span></span>

- [<span data-ttu-id="b38c9-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b38c9-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
