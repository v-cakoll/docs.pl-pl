---
title: Metoda IXCLRDataProcess::StartEnumModules
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d871ca5dfd62dbca309f4ccc3dcedf959033a41e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986560"
---
# <a name="ixclrdataprocessstartenummodules-method"></a>Metoda IXCLRDataProcess::StartEnumModules

Zawiera dojście do wyliczenia modułów procesu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>Parametry

`handle`\
[out] Dojścia wyliczania modułów.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataProcess` interfejs i odnosi się do 24 gniazda tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
**Nagłówek:** Brak  
**Biblioteka:** Brak  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Wyliczenie CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Debugowanie](index.md)
- [Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)
