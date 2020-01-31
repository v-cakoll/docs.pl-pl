---
title: DacpGetModuleAddress Structure
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789206"
---
# <a name="dacpgetmoduleaddress-structure"></a>DacpGetModuleAddress Structure

Definiuje kontener dla żądania adresu modułu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski      | Opis                |
| ----------- | -------------------------- |
| `ModulePtr` | Wskaźnik do modułu. |

## <a name="methods"></a>Metody

| Metoda                                                                                               | Opis                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Żądanie](dacpgetmoduleaddress-request-method.md) | Wykonuje żądanie wypełnienia struktury z danej struktury środowiska uruchomieniowego. |

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, Zdefiniuj strukturę jak określono powyżej, gdzie `CLRDATA_ADDRESS` jest 64-bitową liczbą całkowitą bez znaku.

## <a name="requirements"></a>Wymagania
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Struktury debugowania](debugging-structures.md)
