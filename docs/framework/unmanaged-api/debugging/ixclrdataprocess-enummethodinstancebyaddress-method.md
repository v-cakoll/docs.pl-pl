---
title: IXCLRDataProcess::EnumMethodInstanceByAddress Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a51c709b0b331127b74d98c4dc42e2772fd7f2db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166442"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>IXCLRDataProcess::EnumMethodInstanceByAddress Method

Wylicza wystąpienia metody tego procesu, rozpoczynając od przesunięcia adresu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>Parametry

`handle`\
[in] Dojście do wyliczania wystąpień metody.

`mod`\
[out] Wystąpienie metody wyliczany.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 28 gniazda tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).   
**Nagłówek:** Brak   
**Biblioteka:** Brak   
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a>Zobacz także

- [Wyliczenie CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)
