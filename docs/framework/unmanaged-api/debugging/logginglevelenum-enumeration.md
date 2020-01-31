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
ms.openlocfilehash: 1677798abdb8994d34c82a71e97a2c858209c18e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790389"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum — Wyliczenie
Wskazuje poziom ważności komunikatu opisowego, który jest zapisywana w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`LTraceLevel0`|Komunikat jest poziomem śledzenia równym 0.|  
|`LTraceLevel1`|Komunikat jest poziomem śledzenia 1.|  
|`LTraceLevel2`|Komunikat jest poziomem śledzenia 2.|  
|`LTraceLevel3`|Komunikat jest poziomem śledzenia 3.|  
|`LTraceLevel4`|Komunikat jest poziomem śledzenia 4.|  
|`LStatusLevel0`|Komunikat jest poziomem stanu 0.|  
|`LStatusLevel1`|Komunikat jest poziomem stanu 1.|  
|`LStatusLevel2`|Komunikat jest poziomem stanu 2.|  
|`LStatusLevel3`|Komunikat jest poziomem stanu 3.|  
|`LStatusLevel4`|Komunikat jest poziomem stanu 4.|  
|`LWarningLevel`|Komunikat jest poziomem ostrzegawczym.|  
|`LErrorLevel`|Komunikat jest poziomem błędu.|  
|`LPanicLevel`|Komunikat jest poziomem awaryjnego.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje metodę [ICorDebugManagedCallback:: LogMessage](icordebugmanagedcallback-logmessage-method.md) w celu powiadomienia debugera o zarejestrowaniu zdarzenia przez wątek zarządzany. Środowisko CLR przekazuje wartość wyliczenia `LoggingLevelEnum`, aby wskazać poziom ważności komunikatu, który został zapisany przez wątek zarządzany w dzienniku zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.EventLog>
- [Debugowanie, wyliczenia](debugging-enumerations.md)
