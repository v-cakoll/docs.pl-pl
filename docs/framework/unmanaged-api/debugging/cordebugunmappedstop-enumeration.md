---
title: CorDebugUnmappedStop — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f22c045be9af71644415ae3b6b5e64d3e399dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495438"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop — Wyliczenie
Określa typ niezamapowane kod, który możesz wyzwolić stepper zatrzymania wykonywania kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`STOP_NONE`|Nie zostanie zatrzymana w dowolnego typu niezamapowane kodu.|  
|`STOP_PROLOG`|Zatrzymaj w kodzie prologu.|  
|`STOP_EPILOG`|Zatrzymaj w kod epilogu.|  
|`STOP_NO_MAPPING_INFO`|Zatrzymaj w kodzie, który nie ma mapowania informacji.|  
|`STOP_OTHER_UNMAPPED`|Zatrzymaj w niezamapowane kod, który nie mieści się w prologu, epilogu, nie informacji o mapowaniu lub niezarządzanego kategorii.|  
|`STOP_UNMANAGED`|Zatrzymaj w niezarządzanym kodzie. Ta wartość jest prawidłowa tylko w przypadku debugowania międzyoperacyjnego.|  
|`STOP_ALL`|Zatrzymaj we wszystkich typach niezamapowane kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metodę, aby ustawić flagi określające niezamapowane kodu, w którym stepper zostanie zatrzymane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
