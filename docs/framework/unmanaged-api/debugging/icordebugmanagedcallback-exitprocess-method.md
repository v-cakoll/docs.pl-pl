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
ms.openlocfilehash: 4380b8a3803e164aab7318821a9dbde32ecc3a0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781754"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="a7367-102">ICorDebugManagedCallback::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7367-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="a7367-103">Powiadamia debugera o zakończeniu procesu.</span><span class="sxs-lookup"><span data-stu-id="a7367-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7367-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7367-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7367-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7367-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a7367-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="a7367-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7367-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7367-107">Remarks</span></span>  
 <span data-ttu-id="a7367-108">Nie można kontynuować ze zdarzenia `ExitProcess`.</span><span class="sxs-lookup"><span data-stu-id="a7367-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="a7367-109">To zdarzenie może być wyzwalane asynchronicznie do innych zdarzeń, gdy proces zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="a7367-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="a7367-110">Taka sytuacja może wystąpić, jeśli proces kończy się niepomyślnie, zazwyczaj z powodu pewnej siły zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="a7367-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="a7367-111">Jeśli środowisko uruchomieniowe języka wspólnego (CLR) już wysłało zarządzane wywołanie zwrotne, to zdarzenie zostanie opóźnione do momentu zwrócenia tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a7367-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="a7367-112">Zdarzenie `ExitProcess` jest jedynym zdarzeniem Exit/Unload, które ma zostać wywołane podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="a7367-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7367-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7367-113">Requirements</span></span>  
 <span data-ttu-id="a7367-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7367-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7367-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7367-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7367-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a7367-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7367-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7367-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7367-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7367-118">See also</span></span>

- [<span data-ttu-id="a7367-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7367-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
