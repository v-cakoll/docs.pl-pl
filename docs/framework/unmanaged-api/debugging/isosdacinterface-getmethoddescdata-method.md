---
title: Metoda ISOSDacInterface::GetMethodDescData
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4e32facc65162c4deb853cd507a00126e5f786e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914878"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Metoda ISOSDacInterface::GetMethodDescData

Pobiera dane dla danego wskaźnika MethodDesc.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>Parametry

`methodDesc`\
[in] Adres MethodDesc.

`ip`\
[in] Adres IP metody.

`data`\
[out] Dane skojarzone z MethodDesc w postaci zwracanej przez wewnętrznych interfejsach API.

`cRevertedRejitVersions`\
[out] Numer wersji przywróconym rejit.

`rgRevertedRejitData`\
[out] Dane związane z wersjami przywróconym rejit jak zwrócony z wewnętrznych interfejsach API.

`pcNeededRevertedRejitData`\
[out] Liczba bajtów potrzebnych do przechowania danych skojarzonych z przywróconym wersje ReJit.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `ISOSDacInterface` interfejs i odnosi się do 20 gniazda tabeli metod wirtualnych. Aby móc ich używać, [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) musi być zdefiniowany jako 64-bitowej nieoznaczonej liczby całkowitej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Interfejs ISOSDacInterface](isosdacinterface-interface.md)