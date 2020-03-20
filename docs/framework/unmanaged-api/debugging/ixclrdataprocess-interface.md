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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178377"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess, interfejs

Zawiera metody wykonywania zapytań o proces.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                               | Opis                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Pobiera `AppDomain` w procesie przez jego unikatowy identyfikator.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Zapewnia dojście do wyliczenia modułów procesu.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Wylicza moduły tego procesu.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Zwalnia zasoby używane przez wewnętrzne iteratory używane podczas wyliczania modułu.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Zawiera dojście do wyliczenia `AppDomain` wystąpień metody, począwszy od danego adresu. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Wylicza wystąpienia metody tego procesu, począwszy od przesunięcia adresu.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Zwalnia zasoby używane przez wewnętrzne iteratory używane podczas wyliczania wystąpienia.             |

## <a name="remarks"></a>Uwagi

Ten interfejs znajduje się wewnątrz środowiska wykonawczego i nie jest narażony za pośrednictwem żadnych nagłówków lub plików biblioteki. Jednak jest to interfejs COM, który `IUnknown` wywodzi się z guid, `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` które można uzyskać za pośrednictwem zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też

- [Debugging](index.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
