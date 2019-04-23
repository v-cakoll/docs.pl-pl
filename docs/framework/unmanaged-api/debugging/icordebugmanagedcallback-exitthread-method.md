---
title: ICorDebugManagedCallback::ExitThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37815d8aead1ec89826c13db6f012f2cd17bc792
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132447"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="d7225-102">ICorDebugManagedCallback::ExitThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7225-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="d7225-103">Powiadamia debugera, że zakończył się wątek, który był wykonywany kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d7225-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7225-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7225-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7225-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7225-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d7225-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d7225-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="d7225-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d7225-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7225-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7225-108">Remarks</span></span>  
 <span data-ttu-id="d7225-109">Raz `ExitThread` wywołanie zwrotne jest wywoływane, wątek już nie będą widoczne w wątku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d7225-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7225-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7225-110">Requirements</span></span>  
 <span data-ttu-id="d7225-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7225-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7225-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7225-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7225-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7225-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7225-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7225-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7225-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7225-115">See also</span></span>

- [<span data-ttu-id="d7225-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7225-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
