---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788682"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda
Pobiera wskaźnik natywnej instrukcji dla tego zdarzenia debugowania wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIP`  
 określoną Wskaźnik do wskaźnika instrukcji dla tego zdarzenia debugowania wyjątku. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
 Znaczenie tego wskaźnika instrukcji zależy od typu zdarzenia, jak pokazano w poniższej tabeli.  
  
|Typ zdarzenia|Znaczenie wartości `pStackPointer`|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adres instrukcji powodującej błąd.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adres kodu w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) , w której wykonywanie zostało wznowione, jeśli żaden wyjątek nie został zgłoszony. Wyjątek może lub nie może spowodować innego kodu, takiego jak blok catch klauzuli `try/catch/finally`, do wykonania w tej ramce.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|Adres kodu, w którym `catch` wykonywania procedury obsługi rozpocznie się w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` jest równa 0.|  
  
 Typ zdarzenia jest dostępny w metodzie [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugExceptionDebugEvent, interfejs](icordebugexceptiondebugevent-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
