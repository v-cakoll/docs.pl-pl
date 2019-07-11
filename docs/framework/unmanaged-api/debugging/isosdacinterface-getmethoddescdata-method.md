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
ms.openlocfilehash: ea54fdd83b9470db4a08daceaa695e450f5ca1af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764823"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Metoda ISOSDacInterface::GetMethodDescData

Pobiera dane dla danego wskaźnika MethodDesc.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
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
