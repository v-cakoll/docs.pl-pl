---
title: ICorDebugManagedCallback2::ExceptionUnwind — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faba9631e85ac84ff1517b64e9a3f5567ee7c9dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214798"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="8b5a1-102">ICorDebugManagedCallback2::ExceptionUnwind — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b5a1-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="8b5a1-103">Zawiera powiadomienia o stanie podczas procesu odwijania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5a1-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b5a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b5a1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8b5a1-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8b5a1-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="8b5a1-108">[in] Wartość cordebugexceptionunwindcallbacktype — wyliczenie, który określa zdarzenie, które jest jest sygnalizowane przez wywołania zwrotnego w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8b5a1-109">[in] Wartość [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenie, które określa dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b5a1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b5a1-110">Remarks</span></span>  
 `ExceptionUnwind` <span data-ttu-id="8b5a1-111">nosi nazwę na różnych etapach procesu obsługi wyjątków w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-111">is called at various points during the unwind phase of the exception-handling process.</span></span> `ExceptionUnwind` <span data-ttu-id="8b5a1-112">można wywołać więcej niż jeden raz podczas odwijanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-112">can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="8b5a1-113">Jeśli `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, wskaźnik instrukcji będą znajdować się w ramce liścia wątku w momencie sekwencji przed (może być kilka instrukcji przed) instrukcji, który doprowadził do wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8b5a1-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5a1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b5a1-114">Requirements</span></span>  
 <span data-ttu-id="8b5a1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5a1-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b5a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b5a1-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b5a1-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8b5a1-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8b5a1-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b5a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b5a1-119">See also</span></span>

- [<span data-ttu-id="8b5a1-120">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8b5a1-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="8b5a1-121">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8b5a1-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
