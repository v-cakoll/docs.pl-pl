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
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133723"
---
# <a name="cordebugstatechange-enumeration"></a>Wyliczenie CorDebugStateChange

Opisuje ilość danych buforowanych, które muszą zostać odrzucone na podstawie zmian w procesie.

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
| `PROCESS_RUNNING` | Proces osiągnął nowy stan pamięci przez wykonanie do przodu.            |
| `FLUSH_ALL`       | Pamięć procesu może być arbitralnie inna niż wcześniej. |

## <a name="remarks"></a>Uwagi

 Element członkowski wyliczenia `CorDebugStateChange` jest dostarczany jako argument, gdy debuger wywołuje metodę `ProcessStateChanged` z [ICorDebugProcess4::P rocessstatechanged](icordebugprocess4-processstatechanged-method.md) lub [Metoda ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** CorDebug. idl, CorDebug. h

 **Biblioteka:** CorGuids. lib

 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
- [Debugowanie](index.md)
