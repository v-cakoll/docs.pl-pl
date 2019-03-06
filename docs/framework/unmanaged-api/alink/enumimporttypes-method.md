---
title: EnumImportTypes — Metoda
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355743"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes — Metoda

Wylicza każdy typ w każdym zakresem.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Parametry

`hEnum`\
Dojście dla typu wyliczeniowego.

`dwMax`\
Maksymalna liczba typów do pobrania.

`aTypeDefs`\
Odbiera tokeny typu, aby nie przekroczyć `dwMax`.

`pdwCount`\
Odbiera rzeczywista liczba wpisz `aTypeDefs`.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.

## <a name="requirements"></a>Wymagania

Wymaga alink.h

## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)