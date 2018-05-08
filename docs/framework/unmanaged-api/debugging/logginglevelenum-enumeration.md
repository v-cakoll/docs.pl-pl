---
title: LoggingLevelEnum — Wyliczenie
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 331065d4aae82c66b9ebd82e99427501c3ba8a98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum — Wyliczenie
Wskazuje poziom ważności opisowym komunikatem, które są zapisywane w dzienniku zdarzeń, gdy zarządzanego wątku rejestruje zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`LTraceLevel0`|Komunikat jest poziom śledzenia 0.|  
|`LTraceLevel1`|Komunikat jest poziom śledzenia 1.|  
|`LTraceLevel2`|Komunikat jest poziom śledzenia 2.|  
|`LTraceLevel3`|Komunikat jest poziom śledzenia 3.|  
|`LTraceLevel4`|Komunikat jest poziom śledzenia 4.|  
|`LStatusLevel0`|Komunikat jest poziom stan 0.|  
|`LStatusLevel1`|Komunikat jest poziom stan 1.|  
|`LStatusLevel2`|Komunikat jest stan poziom 2.|  
|`LStatusLevel3`|Komunikat jest poziom stan 3.|  
|`LStatusLevel4`|Komunikat jest poziom stan 4.|  
|`LWarningLevel`|Komunikat jest poziom ostrzeżeń.|  
|`LErrorLevel`|Komunikat jest błąd poziomu.|  
|`LPanicLevel`|Komunikat jest alarm poziomu.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metodę, aby powiadomić debuger zalogował zarządzanego wątku zdarzenia. Środowisko CLR przekazuje wartość `LoggingLevelEnum` wyliczeniu, aby wskazać poziom ważności wiadomości, która zarejestrowała zarządzanych wątków do dziennika zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.EventLog>  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
