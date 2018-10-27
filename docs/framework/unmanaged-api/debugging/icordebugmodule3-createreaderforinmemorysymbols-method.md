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
ms.openlocfilehash: e404228cbc6efb81ed90c135358b1832ddcd8954
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185368"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda
Tworzy czytnik symbolu debugowania dla modułu dynamicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>Parametry  
 Parametr riid  
 [in] IID interfejsu COM do zwrócenia. Zazwyczaj jest to [isymunmanagedreader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Wskaźnik do wskaźnika do interfejsu zwrócone.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie utworzono czytelnika.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Moduł nie jest modułem w pamięci lub dynamicznych.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Symbole nie zostały dostarczone przez aplikację lub nie są jeszcze dostępne.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można utworzyć czytnika.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być również używane do tworzenia obiektu czytnika symboli dla modułów w pamięci (bez dynamiczny), ale tylko wtedy po pierwszych stają się dostępne (wskazywanym przez [updatemodulesymbols — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) wywołania zwrotnego).  
  
 Ta metoda zwraca nowe wystąpienie czytnika za każdym razem, gdy jest on nazywany (takich jak [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). W związku z tym, debuger powinien Zbuforuj wynik i zażądać nowego wystąpienia, tylko wtedy, gdy dane mogły ulec zmianie (to znaczy, gdy [loadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) odebraniu wywołania zwrotnego).  
  
 Moduły dynamiczne nie masz wszystkie symbole, które są dostępne, dopóki nie został załadowany pierwszy typ (wskazane przez [loadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) wywołania zwrotnego).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 4.5, 4, 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRemoteTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
