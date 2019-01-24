---
title: Wyliczenie CorDebugStateChange
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513792"
---
# <a name="cordebugstatechange-enumeration"></a>Wyliczenie CorDebugStateChange
W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`PROCESS_RUNNING`|Proces osiągnięto nowy stan pamięci za pomocą wykonywania do przodu.|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|Pamięć procesu może być dowolnie inny niż wcześniej.|  
  
## <a name="remarks"></a>Uwagi  
 Członek `CorDebugStateChange` wyliczenia jest dostarczana jako argument, gdy wywołuje debugera [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) — metoda  
  
> [!NOTE]
>  To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
