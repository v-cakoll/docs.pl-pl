---
title: CLRDATA_ADDRESS_RANGE, struktura
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274312"
---
# <a name="clrdata_address_range-structure"></a>CLRDATA_ADDRESS_RANGE, struktura

Definiuje zakres adresów.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski         | Opis                     |
| -------------- | ------------------------------- |
| `startAddress` | Adres początkowy zakresu. |
| `endAddress`   | Adres końcowy zakresu.   |

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, Zdefiniuj strukturę jak określono powyżej, gdzie `CLRDATA_ADDRESS` jest 64-bitową liczbą całkowitą bez znaku.

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówki** Brak  
**Biblioteki** Brak  
**.NET Framework wersje:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
