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
ms.openlocfilehash: 2192b5d3b240211c8982eab7539896ea3626a072
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759671"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="195e6-102">ICorDebugManagedCallback::CreateThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="195e6-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="195e6-103">Powiadamia debugera, czy wątek rozpoczęła wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="195e6-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="195e6-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="195e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="195e6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="195e6-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera wątku.</span><span class="sxs-lookup"><span data-stu-id="195e6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="195e6-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="195e6-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="195e6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="195e6-108">Remarks</span></span>  
 <span data-ttu-id="195e6-109">Wątek zostanie umieszczony w pierwszej instrukcji kodu zarządzanego do wykonania.</span><span class="sxs-lookup"><span data-stu-id="195e6-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="195e6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="195e6-110">Requirements</span></span>  
 <span data-ttu-id="195e6-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="195e6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="195e6-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="195e6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="195e6-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="195e6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="195e6-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="195e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195e6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="195e6-115">See also</span></span>

- [<span data-ttu-id="195e6-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="195e6-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
