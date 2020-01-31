---
title: ICorDebugModule, interfejs
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
ms.openlocfilehash: c573e6b768aee1e8b681dcf2e828dc24d409025b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793015"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule, interfejs

Reprezentuje moduł środowiska uruchomieniowego języka wspólnego (CLR), który jest plikiem wykonywalnym lub biblioteką dołączaną dynamicznie (DLL).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](icordebugmodule-createbreakpoint-method.md)|Nie zaimplementowane.|  
|[EnableClassLoadCallbacks, metoda](icordebugmodule-enableclassloadcallbacks-method.md)|Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.|  
|[EnableJITDebugging, metoda](icordebugmodule-enablejitdebugging-method.md)|Określa, czy kompilator just in Time (JIT) zachowuje informacje debugowania dla metod w ramach tego modułu.|  
|[GetAssembly, metoda](icordebugmodule-getassembly-method.md)|Pobiera zawierający go zestaw dla tego modułu.|  
|[GetBaseAddress, metoda](icordebugmodule-getbaseaddress-method.md)|Pobiera adres podstawowy modułu.|  
|[GetClassFromToken, metoda](icordebugmodule-getclassfromtoken-method.md)|Pobiera ICorDebugClass z metadanych.|  
|[GetEditAndContinueSnapshot, metoda](icordebugmodule-geteditandcontinuesnapshot-method.md)|Przestarzałe.|  
|[GetFunctionFromRVA, metoda](icordebugmodule-getfunctionfromrva-method.md)|Nie zaimplementowane.|  
|[GetFunctionFromToken, metoda](icordebugmodule-getfunctionfromtoken-method.md)|Pobiera funkcję określoną przez token metadanych.|  
|[GetGlobalVariableValue, metoda](icordebugmodule-getglobalvariablevalue-method.md)|Pobiera obiekt wartości dla określonej zmiennej globalnej.|  
|[GetMetaDataInterface, metoda](icordebugmodule-getmetadatainterface-method.md)|Pobiera wskaźnik interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.|  
|[GetName, metoda](icordebugmodule-getname-method.md)|Pobiera nazwę pliku modułu.|  
|[GetProcess, metoda](icordebugmodule-getprocess-method.md)|Pobiera proces zawierający dla tego modułu.|  
|[GetSize, metoda](icordebugmodule-getsize-method.md)|Pobiera rozmiar modułu w bajtach.|  
|[GetToken, metoda](icordebugmodule-gettoken-method.md)|Pobiera token dla wpisu tabeli dla tego modułu.|  
|[IsDynamic, metoda](icordebugmodule-isdynamic-method.md)|Wskazuje, czy moduł jest dynamiczny.|  
|[IsInMemory, metoda](icordebugmodule-isinmemory-method.md)|Wskazuje, czy ten moduł istnieje tylko w pamięci.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](icordebug-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
