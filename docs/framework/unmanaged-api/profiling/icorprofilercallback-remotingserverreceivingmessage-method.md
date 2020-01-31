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
ms.openlocfilehash: 6e045a99de9ad30516fd12a7b490e26c860bde7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866016"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="01ede-102">ICorProfilerCallback::RemotingServerReceivingMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="01ede-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="01ede-103">Powiadamia program profilujący, że proces otrzymał zdalne wywołanie metody lub żądanie aktywacji.</span><span class="sxs-lookup"><span data-stu-id="01ede-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ede-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01ede-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ede-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01ede-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="01ede-106">podczas Wartość, która będzie odpowiadała wartości podanej w [ICorProfilerCallback:: RemotingClientSendingMessage —](icorprofilercallback-remotingclientsendingmessage-method.md) w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="01ede-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="01ede-107">Pliki cookie identyfikatorów GUID usług zdalnych są aktywne.</span><span class="sxs-lookup"><span data-stu-id="01ede-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="01ede-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="01ede-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="01ede-109">Pliki cookie identyfikatorów GUID są aktywne w procesie po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="01ede-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="01ede-110">Pozwala to na łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="01ede-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="01ede-111">podczas Wartość, która jest `true`, jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="01ede-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ede-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01ede-112">Remarks</span></span>  
 <span data-ttu-id="01ede-113">Jeśli żądanie komunikatu jest asynchroniczne, żądanie może być serwisowane przez dowolny wątek.</span><span class="sxs-lookup"><span data-stu-id="01ede-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ede-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01ede-114">Requirements</span></span>  
 <span data-ttu-id="01ede-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ede-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ede-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01ede-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01ede-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01ede-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01ede-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ede-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ede-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01ede-119">See also</span></span>

- [<span data-ttu-id="01ede-120">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="01ede-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
