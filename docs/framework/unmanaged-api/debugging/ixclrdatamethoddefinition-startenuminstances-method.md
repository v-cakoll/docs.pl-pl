---
title: 'IXCLRDataMethodDefinition:: StartEnumInstances, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 84e0ad392c5fee8377115427482d80543454fff3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397206"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a>IXCLRDataMethodDefinition:: StartEnumInstances, Metoda

Zapewnia obsługę wyliczania wystąpień metody dla danego elementu `IXCLRDataAppDomain` .

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>Parametry

`appDomain`\
podczas Element AppDomain dla wyliczenia.

`handle`\
określoną Dojście do wyliczania wystąpień.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataMethodDefinition` interfejsu i odpowiada piątemu miejscu tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [CLRDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [IXCLRDataMethodDefinition, interfejs](ixclrdatamethoddefinition-interface.md)
