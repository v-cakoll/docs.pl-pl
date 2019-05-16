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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65225281fe3abaa20e69e96f4cd4d2a4b03a87ce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629944"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction — Metoda

Konfiguruje wywołanie do określonej funkcji.

Ta metoda jest przestarzała w programie .NET Framework 2.0. Użyj [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) zamiast tego.

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
[in] Wskaźnik do obiektu ICorDebugFunction, który określa funkcję, która ma zostać wywołana.

`nArgs`\
[in] Liczba argumentów funkcji.

`ppArgs`\
[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, który określa argument, który zostanie przekazany do funkcji.

## <a name="remarks"></a>Uwagi

Jeśli funkcja znajduje się wirtualny, `CallFunction` wykona wirtualnego wysyłania. Jeśli funkcja znajduje się w domenie innej aplikacji, przejście wystąpi tak długo, jak wszystkie argumenty mają również w tej domenie aplikacji.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug.idl, CorDebug.h

**Biblioteka:** CorGuids.lib

**Wersje programu .NET framework:** 1.1, 1.0

## <a name="see-also"></a>Zobacz także

- [CallParameterizedFunction, metoda](icordebugeval2-callparameterizedfunction-method.md)
