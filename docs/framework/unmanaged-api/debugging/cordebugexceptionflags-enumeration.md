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
ms.openlocfilehash: 198de0aed4e229d7ed8bb1679afc3a0102bd5368
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098465"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags — Wyliczenie
Zawiera dodatkowe informacje o wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Nie istnieje żaden wyjątek.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Wyjątek jest przechwytywany.<br /><br /> Czas wyjątku może być nadal taki, aby debuger nie mógł go przechwycić. Na przykład, jeśli nie istnieje kod zarządzany poniżej bieżącego wywołania zwrotnego lub zdarzenie wyjątku spowodowało z załącznika just-in-Time (JIT), nie można przechwycić wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Nowe wartości można dodać do tego wyliczenia w nowszych wersjach, dlatego należy przygotować kod, który używa `CorDebugExceptionFlags` dla nieoczekiwanych wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
