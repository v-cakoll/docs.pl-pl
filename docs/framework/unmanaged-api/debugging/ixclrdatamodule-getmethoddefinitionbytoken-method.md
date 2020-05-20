---
title: 'IXCLRDataModule:: GetMethodDefinitionByToken, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 074949145be588fc34266a9f2ee501caeeffb9d3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420880"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a>IXCLRDataModule:: GetMethodDefinitionByToken, Metoda

Pobiera definicję metody odpowiadającą danemu tokenowi metadanych.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a>Parametry

`token`\
podczas Token metody.

`methodDefinition`\
określoną Definicja metody.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada 26emu miejscu tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataModule, interfejs](ixclrdatamodule-interface.md)
