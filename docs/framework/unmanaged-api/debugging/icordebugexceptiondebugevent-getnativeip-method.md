---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 82dc892f3081c9f33ff7a2f363c326091f7cf039
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976034"
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
  
|Typ zdarzenia|Znaczenie `pStackPointer` wartości|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adres instrukcji powodującej błąd.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adres kodu w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) , w której wykonywanie zostało wznowione, jeśli żaden wyjątek nie został zgłoszony. Wyjątek może lub nie może spowodować, że inny kod, taki jak blok catch `try/catch/finally` klauzuli, ma być wykonywany w tej ramce.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|Adres kodu, na `catch` którym wykonywanie procedury obsługi rozpocznie się w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP`jest równa 0.|  
  
 Typ zdarzenia jest dostępny w metodzie [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
