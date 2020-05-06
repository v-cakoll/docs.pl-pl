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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795693"
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

| Członek            | Opis                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | Proces osiągnął nowy stan pamięci przez wykonanie do przodu.            |
| `FLUSH_ALL`       | Pamięć procesu może być arbitralnie inna niż wcześniej. |

## <a name="remarks"></a>Uwagi

 Element członkowski `CorDebugStateChange` wyliczenia jest dostarczany jako argument, gdy debuger wywołuje `ProcessStateChanged` metodę z [ICorDebugProcess4::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) lub [Metoda ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** CorDebug. idl, CorDebug. h

 **Biblioteka:** CorGuids. lib

 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie — wyliczenia](debugging-enumerations.md)
- [Debugowanie](index.md)
