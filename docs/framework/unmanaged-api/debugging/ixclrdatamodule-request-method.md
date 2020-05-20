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
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420815"
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

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).
**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [IXCLRDataModule, interfejs](ixclrdatamodule-interface.md)
