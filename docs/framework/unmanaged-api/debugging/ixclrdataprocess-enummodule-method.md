---
title: Metoda IXCLRDataProcess::EnumModule
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a0398d18f9568754231082d63b4c6a2c865d8c6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775274"
---
# <a name="ixclrdataprocessenummodule-method"></a>Metoda IXCLRDataProcess::EnumModule

Wylicza moduły tego procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a>Parametry

`handle`\
[out w] Dojścia wyliczania modułów.

`mod`\
[out] Moduł wyliczany.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 25 gniazda tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Wyliczenie CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [Interfejs IXCLRDataModule](ixclrdatamodule-interface.md)
- [Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)
