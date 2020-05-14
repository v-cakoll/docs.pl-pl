---
title: 'ISOSDacInterface:: GetMethodDescData, Metoda'
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
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396945"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface:: GetMethodDescData, Metoda

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
podczas Adres MethodDesc.

`ip`\
podczas Adres IP metody.

`data`\
określoną Dane skojarzone z MethodDesc jako zwrócone z wewnętrznych interfejsów API.

`cRevertedRejitVersions`\
określoną Liczba przywróconych wersji ReJIT.

`rgRevertedRejitData`\
określoną Dane skojarzone z przywróconymi wersjami ReJIT, które są zwracane z wewnętrznych interfejsów API.

`pcNeededRevertedRejitData`\
określoną Liczba bajtów wymagana do przechowywania danych skojarzonych z przywróconymi wersjami ReJit.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `ISOSDacInterface` interfejsu i odpowiada dwudziestemu miejscu tabeli metody wirtualnej. Aby można było ich używać, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) należy zdefiniować jako 64-bitową liczbę całkowitą bez znaku.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [ISOSDacInterface, interfejs](isosdacinterface-interface.md)
