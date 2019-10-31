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
ms.openlocfilehash: 739b491d343c0eba76160c15719069ffae385f46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097975"
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags — Wyliczenie
Zawiera wartości wpływające na zachowanie kompilatora zarządzanego (just-in-Time).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|Określa, że kompilator ma śledzić dane kompilacji i umożliwia optymalizacje.|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|Określa, że kompilator ma śledzić dane kompilacji, ale wyłącza optymalizacje.|  
|`CORDEBUG_JIT_ENABLE_ENC`|Określa, że kompilator ma śledzić dane kompilacji, wyłącza optymalizacje i umożliwia korzystanie z technologii Edytuj i Kontynuuj.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
