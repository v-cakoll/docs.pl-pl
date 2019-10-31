---
title: ICorDebugManagedCallback::ExitProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4518637eb47acf416a02c045f8ca6f8a90167277
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130786"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="3c8eb-102">ICorDebugManagedCallback::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c8eb-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="3c8eb-103">Powiadamia debugera o zakończeniu procesu.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c8eb-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c8eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c8eb-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="3c8eb-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c8eb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c8eb-107">Remarks</span></span>  
 <span data-ttu-id="3c8eb-108">Nie można kontynuować ze zdarzenia `ExitProcess`.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="3c8eb-109">To zdarzenie może być wyzwalane asynchronicznie do innych zdarzeń, gdy proces zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="3c8eb-110">Taka sytuacja może wystąpić, jeśli proces kończy się niepomyślnie, zazwyczaj z powodu pewnej siły zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="3c8eb-111">Jeśli środowisko uruchomieniowe języka wspólnego (CLR) już wysłało zarządzane wywołanie zwrotne, to zdarzenie zostanie opóźnione do momentu zwrócenia tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="3c8eb-112">Zdarzenie `ExitProcess` jest jedynym zdarzeniem Exit/Unload, które ma zostać wywołane podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="3c8eb-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c8eb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c8eb-113">Requirements</span></span>  
 <span data-ttu-id="3c8eb-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c8eb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c8eb-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3c8eb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c8eb-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3c8eb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c8eb-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c8eb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8eb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c8eb-118">See also</span></span>

- [<span data-ttu-id="3c8eb-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c8eb-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
