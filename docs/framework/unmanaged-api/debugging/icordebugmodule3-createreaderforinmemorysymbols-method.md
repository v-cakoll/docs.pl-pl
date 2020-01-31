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
ms.openlocfilehash: 6596689af6533bb00f41b0d03805b3383ae8c3cc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792944"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="d104b-102">ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="d104b-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="d104b-103">Tworzy czytnik symboli debugowania dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="d104b-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d104b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d104b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="d104b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d104b-105">Parameters</span></span>  
 <span data-ttu-id="d104b-106">riid</span><span class="sxs-lookup"><span data-stu-id="d104b-106">riid</span></span>  
 <span data-ttu-id="d104b-107">podczas Identyfikator IID interfejsu COM do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d104b-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="d104b-108">Zwykle jest to [interfejs ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d104b-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="d104b-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="d104b-109">ppObj</span></span>  
 <span data-ttu-id="d104b-110">określoną Wskaźnik na wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d104b-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d104b-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d104b-111">Return Value</span></span>  
 <span data-ttu-id="d104b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d104b-112">S_OK</span></span>  
 <span data-ttu-id="d104b-113">Pomyślnie utworzono czytnik.</span><span class="sxs-lookup"><span data-stu-id="d104b-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="d104b-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="d104b-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="d104b-115">Moduł nie jest modułem w pamięci lub dynamicznym.</span><span class="sxs-lookup"><span data-stu-id="d104b-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="d104b-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d104b-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="d104b-117">Symbole nie zostały dostarczone przez aplikację lub nie są jeszcze dostępne.</span><span class="sxs-lookup"><span data-stu-id="d104b-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="d104b-118">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="d104b-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d104b-119">Nie można utworzyć czytnika.</span><span class="sxs-lookup"><span data-stu-id="d104b-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d104b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d104b-120">Remarks</span></span>  
 <span data-ttu-id="d104b-121">Ta metoda może również służyć do tworzenia obiektu czytnika symboli dla modułów w pamięci (niedynamicznych), ale tylko po pierwszym udostępnieniu symboli (wskazywanym przez wywołanie zwrotne [metody UpdateModuleSymbols —](icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="d104b-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="d104b-122">Ta metoda zwraca nowe wystąpienie czytnika za każdym razem, gdy jest wywoływana (na przykład [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="d104b-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="d104b-123">W związku z tym debuger powinien buforować wynik i żądać nowego wystąpienia tylko wtedy, gdy dane bazowe mogły ulec zmianie (to oznacza, gdy odbierane jest wywołanie zwrotne [metody LoadClass —](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="d104b-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="d104b-124">Moduły dynamiczne nie mają żadnych symboli dostępnych do momentu załadowania pierwszego typu (wskazanego przez wywołanie zwrotne [metody LoadClass —](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="d104b-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d104b-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d104b-125">Requirements</span></span>  
 <span data-ttu-id="d104b-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d104b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d104b-127">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d104b-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d104b-128">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d104b-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d104b-129">**.NET Framework wersje:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d104b-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d104b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d104b-130">See also</span></span>

- [<span data-ttu-id="d104b-131">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="d104b-131">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="d104b-132">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="d104b-132">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="d104b-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d104b-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
