---
title: "ICorDebugManagedCallback2::Exception — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="a28cc-102">ICorDebugManagedCallback2::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="a28cc-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="a28cc-103">Powiadamia debuger rozpoczęto wyszukiwanie obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a28cc-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a28cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a28cc-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a28cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a28cc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a28cc-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a28cc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a28cc-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a28cc-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="a28cc-108">[in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, zgodnie z ustaleniami `dwEventType` parametru.</span><span class="sxs-lookup"><span data-stu-id="a28cc-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="a28cc-109">Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="a28cc-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="a28cc-110">[in] Liczba całkowita, która określa przesunięcie, zgodnie z ustaleniami `dwEventType` parametru.</span><span class="sxs-lookup"><span data-stu-id="a28cc-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="a28cc-111">Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="a28cc-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="a28cc-112">[in] Wartość wyliczenia CorDebugExceptionCallbackType, który określa typ wywołania zwrotnego tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a28cc-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a28cc-113">[in] Wartość [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenia, która określa dodatkowe informacje o wyjątku</span><span class="sxs-lookup"><span data-stu-id="a28cc-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a28cc-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a28cc-114">Remarks</span></span>  
 <span data-ttu-id="a28cc-115">`Exception` Wywołania zwrotnego jest wywoływana w różnych punktach w fazie wyszukiwania procesu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a28cc-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="a28cc-116">Oznacza to, że jego można wywołać więcej niż raz podczas rozwinięcia Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a28cc-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="a28cc-117">Wyjątek przetwarzanych mogą być pobierane z obiektu ICorDebugThread odwołuje się `pThread` parametru.</span><span class="sxs-lookup"><span data-stu-id="a28cc-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="a28cc-118">Klatek i przesunięcie są określane przez `dwEventType` parametru w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a28cc-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="a28cc-119">Wartość`dwEventType`</span><span class="sxs-lookup"><span data-stu-id="a28cc-119">Value of `dwEventType`</span></span>|<span data-ttu-id="a28cc-120">Wartość`pFrame`</span><span class="sxs-lookup"><span data-stu-id="a28cc-120">Value of `pFrame`</span></span>|<span data-ttu-id="a28cc-121">Wartość`nOffset`</span><span class="sxs-lookup"><span data-stu-id="a28cc-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="a28cc-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a28cc-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="a28cc-123">Ramka, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a28cc-123">The frame that threw the exception.</span></span>|<span data-ttu-id="a28cc-124">Wskaźnik instrukcji w ramce.</span><span class="sxs-lookup"><span data-stu-id="a28cc-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="a28cc-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a28cc-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="a28cc-126">Kod użytkownika ramka najbliższy punkt zwrócony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a28cc-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="a28cc-127">Wskaźnik instrukcji w ramce.</span><span class="sxs-lookup"><span data-stu-id="a28cc-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="a28cc-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="a28cc-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="a28cc-129">Ramki, która zawiera obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="a28cc-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="a28cc-130">Przesunięcie język pośredni (MSIL) firmy Microsoft na początku obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="a28cc-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="a28cc-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="a28cc-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="a28cc-132">NULL</span><span class="sxs-lookup"><span data-stu-id="a28cc-132">NULL</span></span>|<span data-ttu-id="a28cc-133">Niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="a28cc-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a28cc-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a28cc-134">Requirements</span></span>  
 <span data-ttu-id="a28cc-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a28cc-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a28cc-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a28cc-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a28cc-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a28cc-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a28cc-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a28cc-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28cc-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a28cc-139">See Also</span></span>  
 [<span data-ttu-id="a28cc-140">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a28cc-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="a28cc-141">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a28cc-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
