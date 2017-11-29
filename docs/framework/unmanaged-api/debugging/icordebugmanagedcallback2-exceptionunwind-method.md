---
title: "ICorDebugManagedCallback2::ExceptionUnwind — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45b9f5838e4bc98e3f269a2cebd575abfe998a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="c2a10-102">ICorDebugManagedCallback2::ExceptionUnwind — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2a10-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="c2a10-103">Udostępnia powiadomienia o stanie podczas procesu odwijaniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c2a10-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2a10-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2a10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2a10-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c2a10-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c2a10-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c2a10-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c2a10-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="c2a10-108">[in] Wartość wyliczenia CorDebugExceptionUnwindCallbackType określający sygnalizowane trwa przez wywołanie zwrotne w fazie unwind zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c2a10-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c2a10-109">[in] Wartość [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenia, która określa dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c2a10-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a10-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2a10-110">Remarks</span></span>  
 <span data-ttu-id="c2a10-111">`ExceptionUnwind`jest wywoływana w różnych punktach w fazie unwind procesu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c2a10-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="c2a10-112">`ExceptionUnwind`można wywołać więcej niż raz podczas rozwinięcia jeden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c2a10-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="c2a10-113">Jeśli `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, wskaźnik instrukcji będą znajdować się w wątku, w momencie sekwencji przed ramki typu liść (może to być kilka instrukcje przed) instrukcji, które spowodowało wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c2a10-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2a10-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2a10-114">Requirements</span></span>  
 <span data-ttu-id="c2a10-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2a10-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a10-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2a10-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2a10-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2a10-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2a10-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a10-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a10-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2a10-119">See Also</span></span>  
 [<span data-ttu-id="c2a10-120">ICorDebugManagedCallback2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="c2a10-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="c2a10-121">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="c2a10-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
