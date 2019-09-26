---
title: CLRDataSourceType, Wyliczenie
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274096"
---
# <a name="clrdatasourcetype-enumeration"></a>CLRDataSourceType, Wyliczenie

Dostarcza wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a>Elementy członkowskie

| Element członkowski                        | Opis                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | Aby wskazać, że nic nie dotyczy |

## <a name="remarks"></a>Uwagi

To wyliczenie jest przechowywane wewnątrz środowiska uruchomieniowego i nie jest ujawniane za pomocą żadnych nagłówków ani plików bibliotek. Aby go użyć, zdefiniuj Wyliczenie zgodnie z definicją powyżej w kodzie. Jest to również alias `CLRDATA_ENUM` , tak jak wspomniano w przypadku [wspólnych typów danych](../common-data-types-unmanaged-api-reference.md).

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówki** Brak  
**Biblioteki** Brak  
**.NET Framework wersje:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie, wyliczenia](debugging-enumerations.md)
