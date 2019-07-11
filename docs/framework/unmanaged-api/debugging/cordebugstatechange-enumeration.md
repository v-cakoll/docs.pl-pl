---
title: Wyliczenie CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739587"
---
# <a name="cordebugstatechange-enumeration"></a>Wyliczenie CorDebugStateChange

W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.

## <a name="syntax"></a>Składnia

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski            | Opis                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | Proces osiągnięto nowy stan pamięci za pomocą wykonywania do przodu.            |
| `FLUSH_ALL`       | Pamięć procesu może być dowolnie inny niż wcześniej. |

## <a name="remarks"></a>Uwagi

 Członek `CorDebugStateChange` wyliczenia jest dostarczana jako argument, gdy wywołuje debugera `ProcessStateChanged` metody za pomocą [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) lub [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** CorDebug.idl, CorDebug.h

 **Biblioteka:** CorGuids.lib

 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
- [Debugowanie](index.md)
