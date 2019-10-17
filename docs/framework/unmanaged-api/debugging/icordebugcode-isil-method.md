---
title: ICorDebugCode::IsIL — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b7cbadbd1494d5e4d1488dd12296f4f90890127
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395488"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL — Metoda

Pobiera wartość wskazującą, czy ten "ICorDebugCode" reprezentuje kod, który został skompilowany w języku pośrednim firmy Microsoft (MSIL).

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>Parametry

`pbIL`  
[out] `true`, jeśli ten `ICorDebugCode` reprezentuje kod, który został skompilowany w języku MSIL; w przeciwnym razie `false`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
