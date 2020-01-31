---
title: CorDebugJITCompilerFlagsDeprecated — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: 39b90ba35510a5eda7b34e0a80b0e889e5804ca7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778231"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a>CorDebugJITCompilerFlagsDeprecated — Wyliczenie
To wyliczenie jest przestarzałe. Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|Zamiast nich należy używać słów kluczowych `CORDEBUG_JIT_DEFAULT`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
