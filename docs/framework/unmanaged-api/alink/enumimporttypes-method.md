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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448732"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes — Metoda

Wylicza każdy typ w każdym zakresie.

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
Dojście do modułu wyliczającego.

`dwMax`\
Maksymalna liczba typów do pobrania.

`aTypeDefs`\
Odbiera tokeny typu, które nie przekraczają `dwMax`.

`pdwCount`\
Odbiera rzeczywistą liczbę typów w `aTypeDefs`.

## <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli metoda zakończy się pomyślnie.

## <a name="requirements"></a>Wymagania

Wymaga Alink. h

## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
