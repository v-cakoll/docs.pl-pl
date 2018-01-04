---
title: "ICorDebugManagedCallback::ExitThread — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c39a8c92a8c0be8d0607663a833ac7307ca26d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="3591b-102">ICorDebugManagedCallback::ExitThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="3591b-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="3591b-103">Powiadamia debuger zakończył wątku, który został wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3591b-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3591b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3591b-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3591b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3591b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3591b-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="3591b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="3591b-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="3591b-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3591b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3591b-108">Remarks</span></span>  
 <span data-ttu-id="3591b-109">Raz `ExitThread` wywołania zwrotnego jest uruchamiany, wątek nie będzie dłużej widoczny w wątku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3591b-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3591b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3591b-110">Requirements</span></span>  
 <span data-ttu-id="3591b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3591b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3591b-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3591b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3591b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3591b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3591b-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3591b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3591b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3591b-115">See Also</span></span>  
 [<span data-ttu-id="3591b-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3591b-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
