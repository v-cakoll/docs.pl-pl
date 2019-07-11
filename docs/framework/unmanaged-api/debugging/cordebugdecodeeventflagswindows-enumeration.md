---
title: Wyliczenie CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bab7da5855eaf562e55738b489ebf6f62dc45d04
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740224"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a>Wyliczenie CorDebugDecodeEventFlagsWindows
Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|Wskazuje, że zdarzenie debugowania jest wyjątku pierwszej szansy.|  
  
## <a name="remarks"></a>Uwagi  
 [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda zawiera `dwFlags` parametr, który zawiera dodatkowe informacje na temat zdarzeń debugowania, którego wartość jest zależny od architektury docelowej. `CorDebugDecodeEventFlagsWindows` Wyliczenia mogą być używane z zdarzenia debugowania na platformie Windows.  
  
> [!NOTE]
>  To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
