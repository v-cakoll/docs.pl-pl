---
title: 'IXCLRDataProcess:: StartEnumMethodInstancesByAddress, Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394949"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a>IXCLRDataProcess:: StartEnumMethodInstancesByAddress, Metoda

Udostępnia dojście do wyliczenia wystąpień metod, `AppDomain` Zaczynając od danego adresu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a>Parametry

`address`\
podczas Adres pierwszego wystąpienia metody.

`appDomain`\
podczas Obiekt AppDomain wystąpień metody.

`handle`\
określoną Dojście do wyliczania wystąpień metod.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejsu i odnosi się do dwudziestego miejsca w tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Dawaj  
**Biblioteka:** Dawaj  
**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [CLRDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [IXCLRDataProcess, interfejs](ixclrdataprocess-interface.md)
