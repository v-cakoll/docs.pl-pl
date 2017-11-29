---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbab155e783d3b5e40da466fef56633317c67042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="79726-102">ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="79726-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="79726-103">Tworzy czytnika symboli debugowania dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="79726-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79726-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79726-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79726-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79726-105">Parameters</span></span>  
 <span data-ttu-id="79726-106">Parametr riid</span><span class="sxs-lookup"><span data-stu-id="79726-106">riid</span></span>  
 <span data-ttu-id="79726-107">[in] Uzyskanie identyfikatora IID interfejsu COM do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="79726-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="79726-108">Zazwyczaj jest to [ISymUnmanagedReader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="79726-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="79726-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="79726-109">ppObj</span></span>  
 <span data-ttu-id="79726-110">[out] Wskaźnik na wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="79726-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79726-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="79726-111">Return Value</span></span>  
 <span data-ttu-id="79726-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="79726-112">S_OK</span></span>  
 <span data-ttu-id="79726-113">Pomyślnie utworzono czytnika.</span><span class="sxs-lookup"><span data-stu-id="79726-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="79726-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="79726-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="79726-115">Moduł nie jest modułem w pamięci lub dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="79726-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="79726-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79726-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="79726-117">Symbole nie zostały dostarczone przez aplikację lub nie są jeszcze dostępne.</span><span class="sxs-lookup"><span data-stu-id="79726-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="79726-118">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="79726-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="79726-119">Nie można utworzyć czytnika.</span><span class="sxs-lookup"><span data-stu-id="79726-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79726-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79726-120">Remarks</span></span>  
 <span data-ttu-id="79726-121">Tej metody można też używane do tworzenia obiektu czytnika symboli dla modułów w pamięci (z systemem innym niż dynamiczny), ale tylko po najpierw są dostępne symbole (wskazywanym przez [UpdateModuleSymbols — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) wywołanie zwrotne).</span><span class="sxs-lookup"><span data-stu-id="79726-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="79726-122">Ta metoda zwraca nowe wystąpienie czytnika za każdym razem, gdy jest ona wywoływana (takich jak [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span><span class="sxs-lookup"><span data-stu-id="79726-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="79726-123">W związku z tym debuger powinien Zbuforuj wynik i zażądać nowego wystąpienia tylko wtedy, gdy mógł ulec zmianie danych (to znaczy gdy [LoadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) odebraniu wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="79726-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="79726-124">Dynamiczne moduły nie ma żadnych symboli, które są dostępne do momentu załadowania pierwszego typu (wskazywanego przez [LoadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) wywołanie zwrotne).</span><span class="sxs-lookup"><span data-stu-id="79726-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79726-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79726-125">Requirements</span></span>  
 <span data-ttu-id="79726-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79726-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79726-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79726-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79726-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79726-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79726-129">**Wersje programu .NET framework:** 4.5, 4, 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="79726-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79726-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79726-130">See Also</span></span>  
 [<span data-ttu-id="79726-131">ICorDebugRemoteTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="79726-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="79726-132">ICorDebug — interfejs</span><span class="sxs-lookup"><span data-stu-id="79726-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="79726-133">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="79726-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
