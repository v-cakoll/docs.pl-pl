---
title: CorDebugExceptionFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2bf681ed05728a015456e0e4c37157a55f755
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699756"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags — Wyliczenie
Zawiera dodatkowe informacje o wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Nie ma wyjątku.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Wyjątek stanowi interceptable.<br /><br /> Chronometraż wyjątek może nadal być w taki sposób, że debuger nie może przechwycić go. Na przykład jeśli żaden kod zarządzany poniżej bieżącego wywołania zwrotnego, lub zdarzenie wyjątku jest wynikiem just-in-time (JIT) załącznika, wyjątek nie mogą zostać przechwycone.|  
  
## <a name="remarks"></a>Uwagi  
 Nowe wartości mogą być dodawane do tego wyliczenia w nowszych wersjach, więc należy przygotować kod, który używa `CorDebugExceptionFlags` nieoczekiwane wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
