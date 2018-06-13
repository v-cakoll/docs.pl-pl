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
ms.openlocfilehash: 24b01fecc7947d14e36b4411a58d200667b0f2a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415545"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="cd92d-102">ICorDebugManagedCallback::ExitThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd92d-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="cd92d-103">Powiadamia debuger zakończył wątku, który został wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="cd92d-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd92d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd92d-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd92d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd92d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cd92d-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="cd92d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="cd92d-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="cd92d-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd92d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd92d-108">Remarks</span></span>  
 <span data-ttu-id="cd92d-109">Raz `ExitThread` wywołania zwrotnego jest uruchamiany, wątek nie będzie dłużej widoczny w wątku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cd92d-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd92d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd92d-110">Requirements</span></span>  
 <span data-ttu-id="cd92d-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd92d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd92d-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd92d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd92d-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd92d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd92d-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd92d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd92d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd92d-115">See Also</span></span>  
 [<span data-ttu-id="cd92d-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd92d-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
