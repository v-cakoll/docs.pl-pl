---
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress, Metoda'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: d546cda5c68732e75550a3de286089f7df261c91
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420906"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>IXCLRDataMethodInstance:: GetRepresentativeEntryAddress, Metoda

Pobiera najbardziej reprezentatywny adres punktu wejścia dla natywnej kompilacji wszystkich możliwych punktów wejścia dla metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a>Parametry

`addr`\
określoną Adres najbardziej reprezentatywnego macierzystego punktu wejścia dla metody.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią [ `IXCLRDataMethodInstance` interfejsu](ixclrdatamethodinstance-interface.md) i odpowiada dwudziestemu gnieździe tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataMethodInstance, interfejs](ixclrdatamethodinstance-interface.md)
