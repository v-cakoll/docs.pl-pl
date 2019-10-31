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
ms.openlocfilehash: f40030a2034057e83de51a21655a686f30b9ee88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137454"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="38357-102">ICorDebugManagedCallback2::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="38357-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="38357-103">Powiadamia debugera o rozpoczęciu wyszukiwania programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="38357-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38357-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38357-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38357-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38357-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="38357-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą wątek, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="38357-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="38357-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="38357-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="38357-108">podczas Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę określoną przez parametr `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="38357-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="38357-109">Aby uzyskać więcej informacji, zobacz tabelę w sekcji uwagi.</span><span class="sxs-lookup"><span data-stu-id="38357-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="38357-110">podczas Liczba całkowita, która określa przesunięcie, zgodnie z parametrem `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="38357-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="38357-111">Aby uzyskać więcej informacji, zobacz tabelę w sekcji uwagi.</span><span class="sxs-lookup"><span data-stu-id="38357-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="38357-112">podczas Wartość wyliczenia CorDebugExceptionCallbackType —, która określa typ tego wywołania zwrotnego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="38357-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="38357-113">podczas Wartość wyliczenia [CorDebugExceptionFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , która określa dodatkowe informacje o wyjątku</span><span class="sxs-lookup"><span data-stu-id="38357-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38357-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38357-114">Remarks</span></span>  
 <span data-ttu-id="38357-115">Wywołanie zwrotne `Exception` jest wywoływane w różnych punktach w fazie wyszukiwania procesu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="38357-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="38357-116">Oznacza to, że może być wywoływana więcej niż jeden raz podczas odwinięcia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="38357-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="38357-117">Przetwarzany wyjątek można pobrać z obiektu ICorDebugThread, do którego odwołuje się parametr `pThread`.</span><span class="sxs-lookup"><span data-stu-id="38357-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="38357-118">Konkretna ramka i przesunięcie są określane przez parametr `dwEventType` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="38357-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="38357-119">Wartość `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="38357-119">Value of `dwEventType`</span></span>|<span data-ttu-id="38357-120">Wartość `pFrame`</span><span class="sxs-lookup"><span data-stu-id="38357-120">Value of `pFrame`</span></span>|<span data-ttu-id="38357-121">Wartość `nOffset`</span><span class="sxs-lookup"><span data-stu-id="38357-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="38357-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="38357-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="38357-123">Ramka, która wywołała wyjątek.</span><span class="sxs-lookup"><span data-stu-id="38357-123">The frame that threw the exception.</span></span>|<span data-ttu-id="38357-124">Wskaźnik instrukcji w ramce.</span><span class="sxs-lookup"><span data-stu-id="38357-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="38357-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="38357-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="38357-126">Ramka kodu użytkownika najbliżej punktu zgłoszonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="38357-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="38357-127">Wskaźnik instrukcji w ramce.</span><span class="sxs-lookup"><span data-stu-id="38357-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="38357-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="38357-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="38357-129">Ramka, która zawiera procedurę obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="38357-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="38357-130">Przesunięcie języka pośredniego firmy Microsoft (MSIL) od początku procedury obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="38357-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="38357-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="38357-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="38357-132">NULL</span><span class="sxs-lookup"><span data-stu-id="38357-132">NULL</span></span>|<span data-ttu-id="38357-133">Definicji.</span><span class="sxs-lookup"><span data-stu-id="38357-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38357-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38357-134">Requirements</span></span>  
 <span data-ttu-id="38357-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38357-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38357-136">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38357-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38357-137">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38357-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38357-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38357-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38357-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38357-139">See also</span></span>

- [<span data-ttu-id="38357-140">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="38357-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="38357-141">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="38357-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
