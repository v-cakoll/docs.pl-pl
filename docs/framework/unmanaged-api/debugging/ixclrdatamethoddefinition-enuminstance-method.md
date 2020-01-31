---
title: 'IXCLRDataMethodDefinition:: EnumInstance, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790444"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>IXCLRDataMethodDefinition:: EnumInstance, Metoda

Wylicza wystąpienia tej definicji metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a>Parametry

`handle`\
[in. out] Dojście do wyliczania wystąpień.

`instance`\
określoną Wyliczane wystąpienie.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią interfejsu `IXCLRDataMethodDefinition` i odpowiada czwartemu gnieździe tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [CLRDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [IXCLRDataMethodDefinition, interfejs](ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance, interfejs](ixclrdatamethodinstance-interface.md)
