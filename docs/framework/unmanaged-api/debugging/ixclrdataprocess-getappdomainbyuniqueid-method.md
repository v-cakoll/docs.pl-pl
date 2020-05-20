---
title: 'IXCLRDataProcess:: GetAppDomainByUniqueId, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420789"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a>IXCLRDataProcess:: GetAppDomainByUniqueId, Metoda

Pobiera `AppDomain` w procesie na podstawie jego unikatowego identyfikatora.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a>Parametry

`id`\
podczas Unikatowy identyfikator domeny aplikacji

`appDomain`\
określoną Domena aplikacji

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odpowiada dwudziestemu gnieździe tabeli metody wirtualnej. `IXCLRDataAppDomain*`Zwracana wartość jest używana do interakcji z innymi interfejsami API.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).
**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataProcess, interfejs](ixclrdataprocess-interface.md)
