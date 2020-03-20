---
title: CLRDATA_IL_ADDRESS_MAP, struktura
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
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179378"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP, struktura

Definiuje mapowanie IL do adresów.

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

| Członek         | Opis                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | Przesunięcie IL dla zamkniętego zakresu adresów              |
| `startAddress` | Adres początkowy zakresu.                        |
| `endAddress`   | Adres końcowy zakresu.                          |
| `type`         | Typ danych. Ta wartość nie jest obecnie używana |

## <a name="remarks"></a>Uwagi

Ta struktura znajduje się wewnątrz środowiska wykonawczego i nie jest narażona za pośrednictwem żadnych nagłówków lub plików biblioteki. Aby go użyć, zdefiniuj `CLRDATA_ADDRESS` strukturę określoną powyżej, gdzie jest 64-bitową niepodpisaną całkowitej liczby.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak **wersji programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też

- [Wyliczanie CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Debugging](index.md)
- [Struktury debugowania](debugging-structures.md)
