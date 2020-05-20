---
title: 'IXCLRDataMethodInstance:: GetILAddressMap, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0acfa9ffd6f4bc3be567855008dccd08c9c74153
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420919"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a>IXCLRDataMethodInstance:: GetILAddressMap, Metoda

Pobiera informacje o mapowaniu IL to Address.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a>Parametry

`mapLen`\
podczas Długość dostarczonej tablicy map.

`mapNeeded`\
określoną Liczba wpisów mapowania wymaganych przez metodę.

`maps`\
[out, size_is (mapLen)] Tablica do przechowywania wpisów mapy.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataMethodInstance` interfejsu i odpowiada 15emu gnieździe tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataMethodInstance, interfejs](ixclrdatamethodinstance-interface.md)
