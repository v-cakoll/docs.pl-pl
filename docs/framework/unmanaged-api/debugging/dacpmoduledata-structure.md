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
ms.openlocfilehash: e10d1792a8dc0b57ddd121ec09854e8e1824cade
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860802"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData, struktura

Definiuje bufor transportu dla informacji o środowisku uruchomieniowym modułu.

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
| `payLoad` | Bufor ładunku dla dodatkowych informacji modułu używanych przez środowisko uruchomieniowe. |

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, Zdefiniuj strukturę zgodnie z powyższym opisem.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też

- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
