---
title: DacpGetModuleAddress::Request, metoda
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
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860835"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Request, metoda

Wykonuje żądanie wypełnienia struktury z danej struktury środowiska uruchomieniowego.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Parametry

`pDataModule`\
podczas Wskaźnik do modułu danych inicjatora.

## <a name="remarks"></a>Uwagi

Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek. Aby go użyć, najprostszym sposobem jest naśladowanie implementacji:

- Zwróć wartość uzyskaną z wywołania `Request` metody dla `IXCLRDataModule*` parametru o następujących parametrach:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md)\
**Nagłówek:** Dawaj
**Biblioteka:** Dawaj
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz też

- [Debugowanie](index.md)
- [DacpGetModuleAddress, struktura](dacpgetmoduleaddress-structure.md)
