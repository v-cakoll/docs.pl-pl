---
title: ICorDebugCode::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25349f7c8274b818df2cd1bc5d67856e31efecc4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395546"
---
# <a name="icordebugcodegetsize-method"></a>ICorDebugCode::GetSize — Metoda

Pobiera rozmiar (w bajtach) kodu binarnego reprezentowanego przez ten "ICorDebugCode".

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a>Parametry

`pcBytes`  
określoną Wskaźnik do rozmiaru, w bajtach, kodu binarnego, który reprezentuje ten obiekt `ICorDebugCode`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
