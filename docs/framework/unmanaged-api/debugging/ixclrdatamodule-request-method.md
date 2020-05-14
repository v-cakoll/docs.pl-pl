---
title: 'IXCLRDataModule:: Request — Metoda'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 44ee4fc7fc2368b65f6f2fffe6ac239beddc6293
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395270"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule:: Request — Metoda

Żądania wypełnienia buforu podanego za pomocą danych modułu.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Parametry

`reqCode`\
podczas Typ żądania do wysłania.

`inBufferSize`\
[in] rozmiar buforu wejściowego, który ma zostać przesłany.

`inBuffer`\
[in, size_is (inBufferSize)] Wskaźnik buforu dla nieprzetworzonych danych, które mają zostać wysłane w żądaniu.

`outBufferSize`\
podczas Rozmiar buforu wyjściowego.

`outBuffer`\
[out, size_is (outBufferSize)] Wskaźnik buforu używany do przechowywania odpowiedzi na żądanie.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada gnieździe 37th tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).
**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataModule, interfejs](ixclrdatamodule-interface.md)
