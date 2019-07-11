---
title: Metoda ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b30fae0e0a6b6cca64581ecafe78621c8f0068b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754312"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>Metoda ICorDebugExceptionDebugEvent::GetStackPointer
Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStackPointer`  
 [out] Zdarzenie debugowania wskaźnik na adres wskaźnik stosu dla tego wyjątku. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
 Znaczenie tego wskaźnik stosu zależy od typu zdarzenia, jak pokazano w poniższej tabeli.  
  
|Typ zdarzenia|Znaczenie `pStackPointer` wartość|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Wskaźnik stosu ramki, który wygenerował wyjątek.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Wskaźnik stosu ramki kodu użytkownika najbliższy punkt zgłoszony wyjątek.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Wskaźnik stosu ramki, który zawiera program obsługi catch.|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer` jest **null**.|  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
 Typ zdarzenia jest dostępne z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugExceptionDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
