---
title: DacpModuleData, struktura
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179189"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData, struktura

Definiuje bufor transportu dla informacji o czasie wykonywania modułu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>Elementy członkowskie

| Członek    | Opis                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Adres obiektu modułu.                                           |
| `File`    | Wskaźnik do przenośnego pliku wykonywalnego (PE).                       |
| `ilBase`  | Adres bazy załadowanego obrazu.                                 |
| `payLoad` | Bufor ładunku dla dodatkowych informacji o module używanym przez środowisko wykonawcze. |

## <a name="remarks"></a>Uwagi

Ta struktura znajduje się wewnątrz środowiska wykonawczego i nie jest narażona za pośrednictwem żadnych nagłówków lub plików biblioteki. Aby go użyć, należy zdefiniować strukturę, jak określono powyżej.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też

- [Debugging](index.md)
- [Struktury debugowania](debugging-structures.md)
