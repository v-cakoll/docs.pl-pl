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
ms.openlocfilehash: bf59d4e418223fd177bc5e19b173674b78e1f2ba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499925"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="536da-102">ICorProfilerCallback::RemotingServerSendingReply — Metoda</span><span class="sxs-lookup"><span data-stu-id="536da-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="536da-103">Powiadamia program profilujący, że proces zakończył przetwarzanie żądania wywołania metody zdalnej i ma na celu przesłanie odpowiedzi za pośrednictwem kanału.</span><span class="sxs-lookup"><span data-stu-id="536da-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="536da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="536da-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="536da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="536da-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="536da-106">podczas Wskaźnik do identyfikatora GUID, który będzie odpowiadał wartości podanej w [ICorProfilerCallback:: RemotingClientReceivingReply —](icorprofilercallback-remotingclientreceivingreply-method.md) w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="536da-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="536da-107">Pliki cookie identyfikatorów GUID usług zdalnych są aktywne.</span><span class="sxs-lookup"><span data-stu-id="536da-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="536da-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="536da-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="536da-109">Pliki cookie identyfikatorów GUID są aktywne w procesie po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="536da-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="536da-110">Pozwala to na łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="536da-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="536da-111">podczas Wartość, która jest, `true` Jeśli wywołanie jest asynchroniczne; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="536da-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="536da-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="536da-112">Requirements</span></span>  
 <span data-ttu-id="536da-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="536da-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="536da-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="536da-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="536da-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="536da-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="536da-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="536da-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536da-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="536da-117">See also</span></span>

- [<span data-ttu-id="536da-118">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="536da-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
