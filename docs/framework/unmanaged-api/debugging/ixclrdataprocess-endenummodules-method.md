---
title: 'IXCLRDataProcess:: EndEnumModules, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9a7a23e53f5c2bc7d643046830cf335fec780f11
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420841"
---
# <a name="ixclrdataprocessendenummodules-method"></a>IXCLRDataProcess:: EndEnumModules, Metoda

Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania modułu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parametry

`handle`\
określoną Dojście do wyliczania modułów.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada 26emu miejscu tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).
**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataProcess, interfejs](ixclrdataprocess-interface.md)
