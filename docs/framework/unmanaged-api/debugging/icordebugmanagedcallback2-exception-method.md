---
title: ICorDebugManagedCallback2::Exception — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8952b34781045089945e7e72e179e88300b5fdd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103353"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="26022-102">ICorDebugManagedCallback2::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="26022-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="26022-103">Powiadamia debuger rozpoczęto wyszukiwania dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="26022-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26022-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26022-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="26022-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26022-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="26022-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="26022-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="26022-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, na którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="26022-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="26022-108">[in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, zgodnie z ustaleniami `dwEventType` parametru.</span><span class="sxs-lookup"><span data-stu-id="26022-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="26022-109">Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="26022-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="26022-110">[in] Liczba całkowita, która określa przesunięcie, zgodnie z ustaleniami `dwEventType` parametru.</span><span class="sxs-lookup"><span data-stu-id="26022-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="26022-111">Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="26022-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="26022-112">[in] Wartość cordebugexceptioncallbacktype — wyliczenie, który określa typ to wywołanie zwrotne wyjątku.</span><span class="sxs-lookup"><span data-stu-id="26022-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="26022-113">[in] Wartość [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wyliczenie, które określa dodatkowe informacje o wyjątku</span><span class="sxs-lookup"><span data-stu-id="26022-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26022-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26022-114">Remarks</span></span>  
 <span data-ttu-id="26022-115">`Exception` Wywołanie zwrotne jest wywoływane na różnych etapach procesu obsługi wyjątków w fazie wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="26022-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="26022-116">Oznacza to jego może być wywoływana więcej niż jeden raz podczas odwijanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="26022-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="26022-117">Wyjątek przetwarzane można pobrać z zawiera odwołanie do obiektu ICorDebugThread `pThread` parametru.</span><span class="sxs-lookup"><span data-stu-id="26022-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="26022-118">Ramki określonego i przesunięcia, są określane przez `dwEventType` parametru w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="26022-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="26022-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="26022-119">Value of</span></span> `dwEventType`|<span data-ttu-id="26022-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="26022-120">Value of</span></span> `pFrame`|<span data-ttu-id="26022-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="26022-121">Value of</span></span> `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="26022-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="26022-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="26022-123">Ramka, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="26022-123">The frame that threw the exception.</span></span>|<span data-ttu-id="26022-124">Wskaźnik instrukcji w ramce.</span><span class="sxs-lookup"><span data-stu-id="26022-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="26022-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="26022-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="26022-126">Ramka kod użytkownika najbliższy punkt zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="26022-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="26022-127">Wskaźnik instrukcji w ramce.</span><span class="sxs-lookup"><span data-stu-id="26022-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="26022-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="26022-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="26022-129">Ramki, który zawiera program obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="26022-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="26022-130">Microsoft intermediate language (MSIL) Przesunięcie początku obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="26022-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="26022-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="26022-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="26022-132">NULL</span><span class="sxs-lookup"><span data-stu-id="26022-132">NULL</span></span>|<span data-ttu-id="26022-133">Nie zdefiniowano.</span><span class="sxs-lookup"><span data-stu-id="26022-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26022-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26022-134">Requirements</span></span>  
 <span data-ttu-id="26022-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26022-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26022-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26022-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26022-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26022-137">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="26022-138">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="26022-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26022-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26022-139">See also</span></span>

- [<span data-ttu-id="26022-140">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="26022-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="26022-141">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="26022-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
