---
title: Metoda IXCLRDataModule::Request
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
ms.openlocfilehash: 755063ca6da29a2e4733dd653306192ac0434ec0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610603"
---
# <a name="ixclrdatamodulerequest-method"></a>Metoda IXCLRDataModule::Request

Żądania do buforu, biorąc pod uwagę przy użyciu danych modułu wypełniania.

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
[in] Typ do wysłania żądania.

`inBufferSize`\
[in] rozmiar buforu wejściowego, który ma być przekazany w.

`inBuffer`\
[in, size_is(inBufferSize)] Bufor wskaźnik do danych pierwotnych, które mają być wysyłane w żądaniu.

`outBufferSize`\
[in] Rozmiar buforu wyjściowego.

`outBuffer`\
[out, size_is(outBufferSize)] Wskaźnik buforu używany do przechowywania odpowiedzi na żądanie.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `IXCLRDataModule` interfejs i odnosi się do 36 gniazda tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).
**Nagłówek:** Brak **biblioteki:** Brak **wersje programu .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie](index.md)
- [Interfejs IXCLRDataModule](ixclrdatamodule-interface.md)