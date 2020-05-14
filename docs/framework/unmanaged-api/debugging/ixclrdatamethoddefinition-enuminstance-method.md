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
ms.openlocfilehash: 72560de9777b2d826418e63b4a4fcccf1e4fa8b9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396483"
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

Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejsu i odpowiada szóstemu miejscu tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [CLRDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [IXCLRDataMethodDefinition, interfejs](ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance, interfejs](ixclrdatamethodinstance-interface.md)
