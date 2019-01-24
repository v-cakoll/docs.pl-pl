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
ms.openlocfilehash: e72654dc62020e05f18c4d7d4d528617a0cd0c9f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675280"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum — Wyliczenie
Wskazuje poziom ważności opisowy komunikat, który jest zapisywany w dzienniku zdarzeń, gdy wątków zarządzanych rejestruje zdarzenie.  
  
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
|`LStatusLevel0`|Komunikat jest poziom stanu 0.|  
|`LStatusLevel1`|Komunikat jest poziom stanu 1.|  
|`LStatusLevel2`|Komunikat jest poziom stanu 2.|  
|`LStatusLevel3`|Komunikat jest poziom stanu 3.|  
|`LStatusLevel4`|Komunikat jest poziom stanu 4.|  
|`LWarningLevel`|Komunikat jest poziom ostrzeżeń.|  
|`LErrorLevel`|Komunikat jest poziomu błędu.|  
|`LPanicLevel`|Komunikat jest alarm poziom.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metodę, aby powiadomić debugera, że wątków zarządzanych jest rejestrowane zdarzenie. Środowisko CLR przekazuje wartość `LoggingLevelEnum` wyliczenie, aby wskazać poziom ważności komunikatu, który napisał wątków zarządzanych, w dzienniku zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Diagnostics.EventLog>
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
