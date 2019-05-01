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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995036"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="b7285-102">ICorDebugManagedCallback2::ExceptionUnwind — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7285-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="b7285-103">Zawiera powiadomienia o stanie podczas procesu odwijania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7285-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7285-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7285-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7285-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7285-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b7285-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b7285-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b7285-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b7285-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="b7285-108">[in] Wartość cordebugexceptionunwindcallbacktype — wyliczenie, który określa zdarzenie, które jest jest sygnalizowane przez wywołania zwrotnego w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="b7285-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b7285-109">[in] Wartość [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenie, które określa dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7285-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7285-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7285-110">Remarks</span></span>  
 <span data-ttu-id="b7285-111">`ExceptionUnwind` nosi nazwę na różnych etapach procesu obsługi wyjątków w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="b7285-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="b7285-112">`ExceptionUnwind` można wywołać więcej niż jeden raz podczas odwijanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7285-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="b7285-113">Jeśli `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, wskaźnik instrukcji będą znajdować się w ramce liścia wątku w momencie sekwencji przed (może być kilka instrukcji przed) instrukcji, który doprowadził do wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7285-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7285-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7285-114">Requirements</span></span>  
 <span data-ttu-id="b7285-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7285-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7285-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7285-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7285-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7285-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7285-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7285-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7285-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7285-119">See also</span></span>

- [<span data-ttu-id="b7285-120">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7285-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b7285-121">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7285-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
