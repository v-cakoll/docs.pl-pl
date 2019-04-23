---
title: ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfe83707b6354c42a4c3c81e911918b2ea79ec4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108917"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="c1801-102">ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1801-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="c1801-103">Tworzy czytnik symbolu debugowania dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="c1801-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1801-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1801-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1801-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1801-105">Parameters</span></span>  
 <span data-ttu-id="c1801-106">Parametr riid</span><span class="sxs-lookup"><span data-stu-id="c1801-106">riid</span></span>  
 <span data-ttu-id="c1801-107">[in] IID interfejsu COM do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="c1801-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="c1801-108">Zazwyczaj jest to [isymunmanagedreader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c1801-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="c1801-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="c1801-109">ppObj</span></span>  
 <span data-ttu-id="c1801-110">[out] Wskaźnik do wskaźnika do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c1801-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1801-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c1801-111">Return Value</span></span>  
 <span data-ttu-id="c1801-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1801-112">S_OK</span></span>  
 <span data-ttu-id="c1801-113">Pomyślnie utworzono czytelnika.</span><span class="sxs-lookup"><span data-stu-id="c1801-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="c1801-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="c1801-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="c1801-115">Moduł nie jest modułem w pamięci lub dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="c1801-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="c1801-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1801-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="c1801-117">Symbole nie zostały dostarczone przez aplikację lub nie są jeszcze dostępne.</span><span class="sxs-lookup"><span data-stu-id="c1801-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="c1801-118">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="c1801-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c1801-119">Nie można utworzyć czytnika.</span><span class="sxs-lookup"><span data-stu-id="c1801-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1801-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1801-120">Remarks</span></span>  
 <span data-ttu-id="c1801-121">Ta metoda może być również używane do tworzenia obiektu czytnika symboli dla modułów w pamięci (bez dynamiczny), ale tylko wtedy po pierwszych stają się dostępne (wskazywanym przez [updatemodulesymbols — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="c1801-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="c1801-122">Ta metoda zwraca nowe wystąpienie czytnika za każdym razem, gdy jest on nazywany (takich jak [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="c1801-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="c1801-123">W związku z tym, debuger powinien Zbuforuj wynik i zażądać nowego wystąpienia, tylko wtedy, gdy dane mogły ulec zmianie (to znaczy, gdy [loadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) odebraniu wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="c1801-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="c1801-124">Moduły dynamiczne nie masz wszystkie symbole, które są dostępne, dopóki nie został załadowany pierwszy typ (wskazane przez [loadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="c1801-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1801-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1801-125">Requirements</span></span>  
 <span data-ttu-id="c1801-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1801-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1801-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1801-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1801-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1801-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1801-129">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="c1801-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1801-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1801-130">See also</span></span>

- [<span data-ttu-id="c1801-131">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1801-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="c1801-132">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1801-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="c1801-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c1801-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
