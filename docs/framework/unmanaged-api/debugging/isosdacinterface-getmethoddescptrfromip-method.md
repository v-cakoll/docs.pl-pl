---
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP, Metoda'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396930"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>ISOSDacInterface:: GetMethodDescPtrFromIP, Metoda

Pobiera wskaźnik MethodDesc odpowiadającego metodzie zawierającej podanego adresu instrukcji macierzystej.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>Parametry

`ip`\
podczas Adres w ramach metody w czasie wykonywania.

`ppMD`\
określoną Adres `MethodDesc` dla określonej metody.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią [ `ISOSDacInterface` interfejsu](isosdacinterface-interface.md) i odnosi się do 22 gniazda tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [ISOSDacInterface, interfejs](isosdacinterface-interface.md)
