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
ms.openlocfilehash: 820a37c8ca16f4962bf1d72b1f0f404cffd92a1a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499964"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="1bcc4-102">ICorProfilerCallback::RemotingClientSendingMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="1bcc4-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="1bcc4-103">Powiadamia program profilujący, że klient wysyła żądanie do serwera.</span><span class="sxs-lookup"><span data-stu-id="1bcc4-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bcc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bcc4-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bcc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bcc4-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="1bcc4-106">podczas Wartość, która odpowiada wartości podanej w [ICorProfilerCallback:: RemotingServerReceivingMessage —](icorprofilercallback-remotingserverreceivingmessage-method.md) w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="1bcc4-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="1bcc4-107">Pliki cookie identyfikatorów GUID usług zdalnych są aktywne.</span><span class="sxs-lookup"><span data-stu-id="1bcc4-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="1bcc4-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="1bcc4-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="1bcc4-109">Pliki cookie identyfikatorów GUID są aktywne w procesie po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="1bcc4-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="1bcc4-110">Pozwala to na łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="1bcc4-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="1bcc4-111">podczas Wartość, która jest, `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="1bcc4-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bcc4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1bcc4-112">Requirements</span></span>  
 <span data-ttu-id="1bcc4-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bcc4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bcc4-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1bcc4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bcc4-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1bcc4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bcc4-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bcc4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcc4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bcc4-117">See also</span></span>

- [<span data-ttu-id="1bcc4-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1bcc4-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
