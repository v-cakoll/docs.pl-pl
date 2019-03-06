---
title: Metoda IXCLRDataProcess::StartEnumMethodInstancesByAddress
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
ms.openlocfilehash: 8d0494e53705493de814ed4d4caa869e1e8a700f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374573"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a>Metoda IXCLRDataProcess::StartEnumMethodInstancesByAddress

Udostępnia dojścia wyliczania wystąpień metoda `AppDomain` Rozpoczynanie pod danym adresem.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

### <a name="parameters"></a>Parametry

`address`\
[in] Adres pierwszego wystąpienia metody.

`appDomain`\
[in] Element AppDomain wystąpienia metody.

`handle`\
[out] Dojście do wyliczania wystąpień metody.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 27 gniazda tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Wyliczenie CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)
