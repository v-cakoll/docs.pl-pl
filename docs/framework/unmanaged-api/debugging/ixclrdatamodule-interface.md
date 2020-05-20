---
title: IXCLRDataModule, interfejs
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420854"
---
# <a name="ixclrdatamodule-interface"></a>IXCLRDataModule, interfejs

Zapewnia metody wykonywania zapytania o informacje o załadowanym module.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Metody

| Metoda                                                                                                                                | Opis                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [GetMethodDefinitionByToken](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | Pobiera definicję metody odpowiadającą danemu tokenowi metadanych. |
| [Żądanie](ixclrdatamodule-request-method.md)                                       | Żądania wypełnienia buforu podanego za pomocą danych modułu.       |
| [GetVersionId](ixclrdatamodule-getversionid-method.md)                             | Pobiera identyfikator wersji modułu.                                       |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` , który można uzyskać za pomocą zwykłych mechanizmów com.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
