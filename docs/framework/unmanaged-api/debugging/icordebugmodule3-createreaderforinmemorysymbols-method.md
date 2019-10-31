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
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137304"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda
Tworzy czytnik symboli debugowania dla modułu dynamicznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Parametry  
 riid  
 podczas Identyfikator IID interfejsu COM do zwrócenia. Zwykle jest to [interfejs ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 określoną Wskaźnik na wskaźnik do zwracanego interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie utworzono czytnik.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Moduł nie jest modułem w pamięci lub dynamicznym.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Symbole nie zostały dostarczone przez aplikację lub nie są jeszcze dostępne.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można utworzyć czytnika.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może również służyć do tworzenia obiektu czytnika symboli dla modułów w pamięci (niedynamicznych), ale tylko po pierwszym udostępnieniu symboli (wskazywanym przez wywołanie zwrotne [metody UpdateModuleSymbols —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) ).  
  
 Ta metoda zwraca nowe wystąpienie czytnika za każdym razem, gdy jest wywoływana (na przykład [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). W związku z tym debuger powinien buforować wynik i żądać nowego wystąpienia tylko wtedy, gdy dane bazowe mogły ulec zmianie (to oznacza, gdy odbierane jest wywołanie zwrotne [metody LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).  
  
 Moduły dynamiczne nie mają żadnych symboli dostępnych do momentu załadowania pierwszego typu (wskazanego przez wywołanie zwrotne [metody LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRemoteTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
