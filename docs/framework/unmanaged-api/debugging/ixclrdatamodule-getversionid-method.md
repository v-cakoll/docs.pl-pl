---
title: 'IXCLRDataModule:: GetVersionId, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420867"
---
# <a name="ixclrdatamodulegetversionid-method"></a>IXCLRDataModule:: GetVersionId, Metoda

Pobiera identyfikator wersji modułu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a>Parametry

`vid`\
określoną Identyfikator wersji modułu.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada gnieździe 41st tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataModule, interfejs](ixclrdatamodule-interface.md)
