---
title: ICorDebugModule — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 971d6a6a2157c48dcb9105e9f523b1f077098479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129488"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule — Interfejs

Reprezentuje moduł środowiska uruchomieniowego języka wspólnego (CLR), który jest plikiem wykonywalnym lub biblioteką dołączaną dynamicznie (DLL).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Nie zaimplementowane.|  
|[EnableClassLoadCallbacks, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.|  
|[EnableJITDebugging, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Określa, czy kompilator just in Time (JIT) zachowuje informacje debugowania dla metod w ramach tego modułu.|  
|[GetAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Pobiera zawierający go zestaw dla tego modułu.|  
|[GetBaseAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Pobiera adres podstawowy modułu.|  
|[GetClassFromToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Pobiera ICorDebugClass z metadanych.|  
|[GetEditAndContinueSnapshot, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Przestarzałe.|  
|[GetFunctionFromRVA, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Nie zaimplementowane.|  
|[GetFunctionFromToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Pobiera funkcję określoną przez token metadanych.|  
|[GetGlobalVariableValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Pobiera obiekt wartości dla określonej zmiennej globalnej.|  
|[GetMetaDataInterface, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Pobiera wskaźnik interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Pobiera nazwę pliku modułu.|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Pobiera proces zawierający dla tego modułu.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Pobiera rozmiar modułu w bajtach.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Pobiera token dla wpisu tabeli dla tego modułu.|  
|[IsDynamic, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Wskazuje, czy moduł jest dynamiczny.|  
|[IsInMemory, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Wskazuje, czy ten moduł istnieje tylko w pamięci.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
