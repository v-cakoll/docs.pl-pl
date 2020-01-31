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
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790373"
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
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Udostępnia dojście do wyliczenia wystąpień metody `AppDomain`, rozpoczynając od danego adresu. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.             |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7`, który można uzyskać za pomocą zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).   
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
