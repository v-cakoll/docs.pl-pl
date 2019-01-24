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
ms.openlocfilehash: e56f837c4d3362ec6e71030e4fb475df42b9fba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639961"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Metoda ISOSDacInterface::GetMethodDescData

Pobiera dane dla danego [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a>Parametry

`methodDesc` [in] Adres MethodDesc.

`ip` [in] Adres IP metody.

`data` [out] Dane skojarzone z MethodDesc w postaci zwracanej przez wewnętrznych interfejsach API. Struktura wymaga co najmniej 168 bajtów.

`cRevertedRejitVersions` [out] Numer wersji przywróconym rejit.

`rgRevertedRejitData` [out] Dane związane z wersjami przywróconym rejit jak zwrócony z wewnętrznych interfejsach API. Struktura wymaga co najmniej 24 bajtów.

`pcNeededRevertedRejitData` [out] Liczba bajtów potrzebnych do przechowania danych skojarzonych z przywróconym wersje ReJit.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `ISOSDacInterface` interfejs i odnosi się do 20 gniazda tabeli metod wirtualnych. Również `CLRDATA_ADDRESS` są 64-bitowej nieoznaczonej liczby całkowitej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Interfejs ISOSDacInterface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
