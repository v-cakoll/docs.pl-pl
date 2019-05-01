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
ms.openlocfilehash: ff74a7acb5cc84c177f083c19402cd78977aeab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775248"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess, interfejs

Udostępnia metody do wykonywania zapytań informacji dotyczących procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                               | Opis                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Pobiera `AppDomain` w procesie według unikatowego identyfikatora.                                              |
| [StartEnumModules](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | Zawiera dojście do wyliczenia modułów procesu.                                        |
| [EnumModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | Wylicza moduły tego procesu.                                                         |
| [EndEnumModules](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania modułu.               |
| [StartEnumMethodInstancesByAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Udostępnia dojścia wyliczania wystąpień metoda `AppDomain` Rozpoczynanie pod danym adresem. |
| [EnumMethodInstanceByAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.                  |
| [EndEnumMethodInstancesByAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Zwalnia zasoby używane przez Iteratory wewnętrzny używany podczas wyliczania wystąpień.             |

## <a name="remarks"></a>Uwagi

Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki. Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).   
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
