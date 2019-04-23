---
title: DacpReJitData, struktura
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122801"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData, struktura

Definiuje podstawowe informacje o danej metody Instrumentacji profilera.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski           | Opis                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | Numer poprawki ReJit dla metody.                                                          |
| `flags`          | Flaga wskazująca bieżący stan metody ReJit instrumentacji dla danej wersji. |
| `NativeCodeAddr` | Adres podstawowy implementacji rejitted metody.                                         |

## <a name="remarks"></a>Uwagi

Ta struktura znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki. Aby go użyć, definiują strukturę, jak określono powyżej. Struktura również musi być zdefiniowane przy użyciu `ms_struct` pakowania, jeśli nie za pomocą kompilatorów Microsoft.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
