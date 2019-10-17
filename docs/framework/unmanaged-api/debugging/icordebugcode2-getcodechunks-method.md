---
title: ICorDebugCode2::GetCodeChunks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d64773aa0d35f2e97232576d145dfcba624812ec
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395531"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks — Metoda

Pobiera fragmenty kodu, z których składa się ten obiekt kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>Parametry

`cbufSize`  
podczas Rozmiar tablicy `chunks`.

`pcnumChunks`  
określoną Liczba fragmentów zwróconych w tablicy `chunks`.

`chunks`  
określoną Tablica struktur "CodeChunkInfo —", z których każdy reprezentuje pojedynczy fragment kodu. Jeśli wartość `cbufSize` to 0, ten parametr może mieć wartość null.

## <a name="remarks"></a>Uwagi

Fragmenty kodu nie nakładają się na siebie i będą podążać za kolejnością, w jakiej zostałyby połączone przez [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md). Obiekt kodu języka pośredniego (MSIL) firmy Microsoft w .NET Framework w wersji 2,0 będzie obejmował pojedynczy fragment kodu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
