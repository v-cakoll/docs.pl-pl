---
title: IXCLRDataMethodDefinition, interfejs
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790428"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition, interfejs

Zapewnia metody wykonywania zapytań dotyczących informacji o definicji metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

Poniżej przedstawiono metody dostępne w interfejsie.

| Metoda                                                                                                                          | Opis                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Zapewnia obsługę wyliczania wystąpień metody dla danego `IXCLRDataAppDomain`. |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Wylicza wystąpienia tej definicji metody.                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Zwalnia zasoby używane przez Iteratory wewnętrzne używane podczas wyliczania wystąpień.         |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97`, który można uzyskać za pomocą zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
