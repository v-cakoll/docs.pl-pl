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
ms.workload: dotnet
ms.openlocfilehash: 2838c6c1fe8641e343fac1a3efa82a39ee177abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols — Metoda
Tworzy czytnika symboli debugowania dla modułu dynamicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>Parametry  
 Parametr riid  
 [in] Uzyskanie identyfikatora IID interfejsu COM do zwrócenia. Zazwyczaj jest to [ISymUnmanagedReader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Wskaźnik na wskaźnik do interfejsu zwrócony.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie utworzono czytnika.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Moduł nie jest modułem w pamięci lub dynamicznych.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Symbole nie zostały dostarczone przez aplikację lub nie są jeszcze dostępne.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można utworzyć czytnika.  
  
## <a name="remarks"></a>Uwagi  
 Tej metody można też używane do tworzenia obiektu czytnika symboli dla modułów w pamięci (z systemem innym niż dynamiczny), ale tylko po najpierw są dostępne symbole (wskazywanym przez [UpdateModuleSymbols — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) wywołanie zwrotne).  
  
 Ta metoda zwraca nowe wystąpienie czytnika za każdym razem, gdy jest ona wywoływana (takich jak [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)). W związku z tym debuger powinien Zbuforuj wynik i zażądać nowego wystąpienia tylko wtedy, gdy mógł ulec zmianie danych (to znaczy gdy [LoadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) odebraniu wywołania zwrotnego).  
  
 Dynamiczne moduły nie ma żadnych symboli, które są dostępne do momentu załadowania pierwszego typu (wskazywanego przez [LoadClass — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) wywołanie zwrotne).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 4.5, 4, 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRemoteTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
