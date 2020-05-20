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
ms.openlocfilehash: 0b1c982b25af9edea76a038b4314b4bd608f07df
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420893"
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

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , który można uzyskać za pomocą zwykłych mechanizmów com.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
