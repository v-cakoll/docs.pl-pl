---
title: CLRDATA_IL_ADDRESS_MAP Structure
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274294"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP Structure

Definiuje mapowanie IL to Address.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski         | Opis                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | Przesunięcie IL dla zawartego zakresu adresów              |
| `startAddress` | Adres początkowy zakresu.                        |
| `endAddress`   | Adres końcowy zakresu.                          |
| `type`         | Typ danych. Ta wartość nie jest obecnie używana |

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, Zdefiniuj strukturę jak określono powyżej, gdzie `CLRDATA_ADDRESS` jest 64-bitową liczbą całkowitą bez znaku.

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówki** Brak  
**Biblioteki** Brak   
**.NET Framework wersje:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [CLRDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
