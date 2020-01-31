---
title: IXCLRDataMethodInstance, interfejs
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790409"
---
# <a name="ixclrdatamethodinstance-interface"></a>IXCLRDataMethodInstance, interfejs

Zapewnia metody wykonywania zapytań dotyczących informacji o wystąpieniu metody.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                  | Opis                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [GetILAddressMap](ixclrdatamethodinstance-getiladdressmap-method.md) | Pobiera informacje o mapowaniu IL to Address. |
| [GetRepresentativeEntryAddress](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | Pobiera najbardziej reprezentatywny adres punktu wejścia dla natywnej kompilacji wszystkich możliwych punktów wejścia dla metody. |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5`, który można uzyskać za pomocą zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
