---
title: CorDebugJITCompilerFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5835da6ee20673c2662f1166d304a45ca3e9daeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags — Wyliczenie
Zawiera wartości, które wpływają na zachowanie zarządzanych kompilatora just in time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|Określa, czy kompilator powinien śledzą dane dotyczące kompilacji i umożliwia optymalizacji.|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|Określa, czy kompilator powinien śledzenia danych kompilacji, ale wyłącza optymalizacje.|  
|`CORDEBUG_JIT_ENABLE_ENC`|Określa, że kompilator powinien śledzenia danych kompilacji, wyłącza optymalizacje, i umożliwia Edytuj i Kontynuuj technologii.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
