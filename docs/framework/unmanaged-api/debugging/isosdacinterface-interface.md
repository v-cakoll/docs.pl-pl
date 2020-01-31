---
title: ISOSDacInterface, interfejs
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790481"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface, interfejs

Zapewnia metody pomocnika do uzyskiwania dostępu do danych z `SOS`.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                               | Opis                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | Pobiera dane dla danego wskaźnika MethodDesc. |
| [GetMethodDescPtrFromIP](isosdacinterface-getmethoddescptrfromip-method.md) | Pobiera wskaźnik MethodDesc odpowiadającego metodzie zawierającej podanego adresu instrukcji macierzystej. |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| Pobiera dane odpowiadające modułowi załadowanemu pod danym adresem. |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `436f00f2-b42a-4b9f-870c-e73db66ae930`, który można uzyskać za pomocą zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
