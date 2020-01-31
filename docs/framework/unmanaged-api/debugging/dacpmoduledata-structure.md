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
ms.openlocfilehash: b46a04d67f59c5031b5bd195cef4cc2275e1e5e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793806"
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

| Element członkowski    | Opis                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Adres obiektu modułu.                                           |
| `File`    | Wskaźnik do przenośnego pliku wykonywalnego (PE).                       |
| `ilBase`  | Adres bazy załadowanego obrazu.                                 |
| `payLoad` | Bufor ładunku dla dodatkowych informacji modułu używanych przez środowisko uruchomieniowe. |

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, Zdefiniuj strukturę zgodnie z powyższym opisem.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
