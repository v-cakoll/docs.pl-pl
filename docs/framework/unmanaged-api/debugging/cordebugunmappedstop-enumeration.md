---
title: "CorDebugUnmappedStop — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5700a9a058a349ea70020bafb7d4bed73d1f53f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop — Wyliczenie
Określa typ Niemapowane kodu, które mogą wyzwalać zatrzymania wykonywania kodu przez stepper.  
  
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
|`STOP_NONE`|Nie zostanie zatrzymana w typu Niemapowane kodu.|  
|`STOP_PROLOG`|Zatrzymaj w prologu kodu.|  
|`STOP_EPILOG`|Kod epilogu zatrzyma.|  
|`STOP_NO_MAPPING_INFO`|Zatrzymanie w kodzie, który nie ma mapowania informacji.|  
|`STOP_OTHER_UNMAPPED`|Zatrzymaj Niemapowane kodu, który nie mieści się w prologu, epilogu, nie informacje dotyczące mapowania lub niezarządzane kategorii.|  
|`STOP_UNMANAGED`|Zatrzymaj za pomocą kodu niezarządzanego. Ta wartość jest prawidłowa tylko w przypadku debugowania międzyoperacyjnego.|  
|`STOP_ALL`|Zatrzymaj we wszystkich typach Niemapowane kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metody można ustawić flagi określające Niemapowane kodu, w którym stepper zostanie zatrzymane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
