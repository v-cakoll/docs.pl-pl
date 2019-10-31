---
title: ICorDebugEval::CallFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085157"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction — Metoda

Konfiguruje wywołanie do określonej funkcji.

Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj [ICorDebugEval2:: CallParameterizedFunction —](icordebugeval2-callparameterizedfunction-method.md) .

## <a name="syntax"></a>Składnia

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>Parametry

`pFunction`\
podczas Wskaźnik do obiektu ICorDebugFunction, który określa funkcję, która ma zostać wywołana.

`nArgs`\
podczas Liczba argumentów dla funkcji.

`ppArgs`\
podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który określa argument, który ma zostać przesłany do funkcji.

## <a name="remarks"></a>Uwagi

Jeśli funkcja jest wirtualna, `CallFunction` przeprowadzi wirtualną wysyłkę. Jeśli funkcja znajduje się w innej domenie aplikacji, przejście zostanie przeprowadzone tak długo, jak wszystkie argumenty są również w tej domenie aplikacji.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**.NET Framework wersje:** 1,1, 1,0

## <a name="see-also"></a>Zobacz także

- [CallParameterizedFunction, metoda](icordebugeval2-callparameterizedfunction-method.md)
