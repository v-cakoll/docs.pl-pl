---
title: DacpGetModuleAddress::Metoda żądania
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102910"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Metoda żądania

Wykonuje żądanie, aby wypełnić strukturę z danej struktury środowiska wykonawczego.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Parametry

`pDataModule`\
[w] Wskaźnik do modułu danych źródłowych.

## <a name="remarks"></a>Uwagi

Ta struktura znajduje się wewnątrz środowiska wykonawczego i nie jest narażona za pośrednictwem żadnych nagłówków lub plików biblioteki. Aby go użyć, najprostszym sposobem jest naśladowanie implementacji:

- Zwraca wartość uzyskaną `Request` z wywołania metody na parametr z `IXCLRDataModule*` następującymi parametrami:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md)\
**Nagłówek:** Brak\
**Biblioteka:** Brak\
**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz też

- [Debugowanie](index.md)
- [Struktura DacpGetModuleAddress](dacpgetmoduleaddress-structure.md)
