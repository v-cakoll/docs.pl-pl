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
ms.openlocfilehash: fa317e1217ac0a9ca46bfeb312446534b1fca63a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131561"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="753c2-102">ICorDebugManagedCallback2::ExceptionUnwind — Metoda</span><span class="sxs-lookup"><span data-stu-id="753c2-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="753c2-103">Udostępnia powiadomienie o stanie podczas procesu odwracania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="753c2-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="753c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="753c2-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="753c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="753c2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="753c2-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą wątek, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="753c2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="753c2-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="753c2-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="753c2-108">podczas Wartość wyliczenia CorDebugExceptionUnwindCallbackType —, która określa zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="753c2-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="753c2-109">podczas Wartość wyliczenia [CorDebugExceptionFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , która określa dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="753c2-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="753c2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="753c2-110">Remarks</span></span>  
 <span data-ttu-id="753c2-111">`ExceptionUnwind` jest wywoływana w różnych punktach w fazie unwind procesu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="753c2-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="753c2-112">`ExceptionUnwind` może być wywoływana więcej niż jeden raz podczas odwinięcia pojedynczego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="753c2-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="753c2-113">Jeśli `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, wskaźnik instrukcji będzie znajdować się w ramce liścia wątku, w punkcie sekwencji przed (może to być kilka instrukcji przed) instrukcją, która doprowadziła do wyjątku.</span><span class="sxs-lookup"><span data-stu-id="753c2-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="753c2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="753c2-114">Requirements</span></span>  
 <span data-ttu-id="753c2-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="753c2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="753c2-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="753c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="753c2-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="753c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="753c2-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="753c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753c2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="753c2-119">See also</span></span>

- [<span data-ttu-id="753c2-120">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="753c2-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="753c2-121">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="753c2-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
