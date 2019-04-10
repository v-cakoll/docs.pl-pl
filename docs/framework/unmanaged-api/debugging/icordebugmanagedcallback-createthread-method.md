---
title: ICorDebugManagedCallback::CreateThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c48e92c73347957d8acc5c209f6f5473e9e18524
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223254"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="7ab29-102">ICorDebugManagedCallback::CreateThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ab29-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="7ab29-103">Powiadamia debugera, czy wątek rozpoczęła wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7ab29-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ab29-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ab29-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7ab29-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera wątku.</span><span class="sxs-lookup"><span data-stu-id="7ab29-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="7ab29-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="7ab29-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab29-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ab29-108">Remarks</span></span>  
 <span data-ttu-id="7ab29-109">Wątek zostanie umieszczony w pierwszej instrukcji kodu zarządzanego do wykonania.</span><span class="sxs-lookup"><span data-stu-id="7ab29-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab29-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ab29-110">Requirements</span></span>  
 <span data-ttu-id="7ab29-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab29-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ab29-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ab29-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ab29-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7ab29-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7ab29-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ab29-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ab29-115">See also</span></span>

- [<span data-ttu-id="7ab29-116">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7ab29-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
