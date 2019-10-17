---
title: ICorDebugCodeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac3fc157543f2990c7c9f9917140b35f8948108e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395480"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next — Metoda

Pobiera określoną liczbę wystąpień "ICorDebugCode" z wyliczenia, rozpoczynając od bieżącego położenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>Parametry

`celt`  
podczas Liczba wystąpień `ICorDebugCode` do pobrania.

`values`  
określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugCode`.

`pceltFetched`  
określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugCode`. Ta wartość może być równa null, jeśli `celt` to jeden.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
