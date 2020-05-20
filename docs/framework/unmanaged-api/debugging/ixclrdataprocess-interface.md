---
title: IXCLRDataProcess, interfejs
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6a6def8fc10f04b89aa8d8c735025b01f9b6ddfb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420763"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess, interfejs

Dostarcza metody do wykonywania zapytań dotyczących informacji o procesie.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                               | Opis                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Pobiera `AppDomain` w procesie według jego unikatowego identyfikatora.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Udostępnia dojście do wyliczenia modułów procesu.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Wylicza moduły tego procesu.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania modułu.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Udostępnia dojście do wyliczenia wystąpień metod, `AppDomain` Zaczynając od danego adresu. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.             |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , który można uzyskać za pomocą zwykłych mechanizmów com.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
