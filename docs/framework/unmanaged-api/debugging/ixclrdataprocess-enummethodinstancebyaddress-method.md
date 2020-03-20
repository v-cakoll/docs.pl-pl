---
title: Metoda IXCLCLDATaProcess::EnumMethodInstanceByAddress Metoda
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
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176659"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>Metoda IXCLCLDATaProcess::EnumMethodInstanceByAddress Metoda

Wylicza wystąpienia metody tego procesu, począwszy od przesunięcia adresu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>Parametry

`handle`\
[w] Dojście do wyliczania wystąpień metody.

`mod`\
[na zewnątrz] Wystąpienie metody wyliczonej.

## <a name="remarks"></a>Uwagi

Podana metoda jest `IXCLRDataProcess` częścią interfejsu i odpowiada 28-cie gniazdo tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).
**Nagłówek:** Brak **biblioteki:** Brak **wersji programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz też

- [Wyliczanie CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Debugging](index.md)
- [IXCLRDataProcess, interfejs](ixclrdataprocess-interface.md)
