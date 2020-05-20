---
title: 'IXCLRDataProcess:: StartEnumModules, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420724"
---
# <a name="ixclrdataprocessstartenummodules-method"></a>IXCLRDataProcess:: StartEnumModules, Metoda

Udostępnia dojście do wyliczenia modułów procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>Parametry

`handle`\
określoną Dojście do wyliczania modułów.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 24emu miejscu tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [CLRDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [IXCLRDataProcess, interfejs](ixclrdataprocess-interface.md)
