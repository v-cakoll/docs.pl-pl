---
title: "ICorDebugManagedCallback::Exception — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b964f38501822360e6fc63600f7854c9a90f094c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="b0354-102">ICorDebugManagedCallback::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0354-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="b0354-103">Powiadamia debugera, czy wyjątek został zgłoszony z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b0354-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0354-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0354-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0354-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0354-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b0354-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b0354-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b0354-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b0354-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="b0354-108">[in] Jeśli ta wartość jest `false`, wyjątek jeszcze nie zostały przetworzone przez aplikację, a w przeciwnym, jest nieobsługiwany wyjątek i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="b0354-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0354-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0354-109">Remarks</span></span>  
 <span data-ttu-id="b0354-110">Określony wyjątek można pobrać z obiektu wątku.</span><span class="sxs-lookup"><span data-stu-id="b0354-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0354-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0354-111">Requirements</span></span>  
 <span data-ttu-id="b0354-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0354-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0354-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0354-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0354-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0354-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0354-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0354-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0354-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0354-116">See Also</span></span>  
 [<span data-ttu-id="b0354-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0354-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
