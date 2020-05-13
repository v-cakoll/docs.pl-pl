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
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212246"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule, interfejs

Reprezentuje moduł środowiska uruchomieniowego języka wspólnego (CLR), który jest plikiem wykonywalnym lub biblioteką dołączaną dynamicznie (DLL).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint — Metoda](icordebugmodule-createbreakpoint-method.md)|Nie zaimplementowano.|  
|[EnableClassLoadCallbacks, metoda](icordebugmodule-enableclassloadcallbacks-method.md)|Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.|  
|[EnableJITDebugging, metoda](icordebugmodule-enablejitdebugging-method.md)|Określa, czy kompilator just in Time (JIT) zachowuje informacje debugowania dla metod w ramach tego modułu.|  
|[GetAssembly, metoda](icordebugmodule-getassembly-method.md)|Pobiera zawierający go zestaw dla tego modułu.|  
|[GetBaseAddress — Metoda](icordebugmodule-getbaseaddress-method.md)|Pobiera adres podstawowy modułu.|  
|[GetClassFromToken — Metoda](icordebugmodule-getclassfromtoken-method.md)|Pobiera ICorDebugClass z metadanych.|  
|[GetEditAndContinueSnapshot, metoda](icordebugmodule-geteditandcontinuesnapshot-method.md)|Przestarzałe.|  
|[GetFunctionFromRVA, metoda](icordebugmodule-getfunctionfromrva-method.md)|Nie zaimplementowano.|  
|[GetFunctionFromToken — Metoda](icordebugmodule-getfunctionfromtoken-method.md)|Pobiera funkcję określoną przez token metadanych.|  
|[GetGlobalVariableValue, metoda](icordebugmodule-getglobalvariablevalue-method.md)|Pobiera obiekt wartości dla określonej zmiennej globalnej.|  
|[GetMetaDataInterface, metoda](icordebugmodule-getmetadatainterface-method.md)|Pobiera wskaźnik interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.|  
|[GetName — Metoda](icordebugmodule-getname-method.md)|Pobiera nazwę pliku modułu.|  
|[GetProcess — Metoda](icordebugmodule-getprocess-method.md)|Pobiera proces zawierający dla tego modułu.|  
|[GetSize — Metoda](icordebugmodule-getsize-method.md)|Pobiera rozmiar modułu w bajtach.|  
|[GetToken — Metoda](icordebugmodule-gettoken-method.md)|Pobiera token dla wpisu tabeli dla tego modułu.|  
|[IsDynamic, metoda](icordebugmodule-isdynamic-method.md)|Wskazuje, czy moduł jest dynamiczny.|  
|[IsInMemory, metoda](icordebugmodule-isinmemory-method.md)|Wskazuje, czy ten moduł istnieje tylko w pamięci.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebug — Interfejs](icordebug-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
