---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868333"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3, Metoda

Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID. Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a>Parametry

- `ip`

  \[w] wskaźnik instrukcji w kodzie zarządzanym.

- `pFunctionId`

  \[out] identyfikator funkcji.

- `pReJitId`

  \[out] tożsamość funkcji ponownie skompilowanej w trybie JIT.

## <a name="remarks"></a>Uwagi

Ta metoda działa w przypadku metod dynamicznych i niedynamicznych. Jest to nadzbiór [GetFunctionFromIP2 —](icorprofilerinfo4-getfunctionfromip2-method.md), który działa tylko w przypadku funkcji z metadanymi.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo8, interfejs](icorprofilerinfo8-interface.md)
