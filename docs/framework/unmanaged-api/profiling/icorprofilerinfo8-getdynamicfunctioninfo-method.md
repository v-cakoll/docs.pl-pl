---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9b5059d9e4bf9b79dc67664c7a7971041d1cf35b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861687"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo, Metoda

Pobiera informacje o metodach dynamicznych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a>Parametry

- `functionId`

  \[in) identyfikator funkcji, dla której mają zostać pobrane informacje.

- `moduleId`

  \[w] wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.

- `ppvSig`

  \[out] wskaźnik do podpisu dla funkcji.

- `pbSig`

  \[out] wskaźnik do liczby bajtów dla sygnatury funkcji.

- `cchName`

  \[] maksymalny rozmiar tablicy `wszName`.

- `pcchName`

  \[out] liczba znaków w tablicy `wszName`.

- `wszName`

  \[out] tablica `WCHAR`, która jest nazwą funkcji (jeśli taka istnieje).

## <a name="remarks"></a>Uwagi

Niektóre metody, takie jak IL repliks lub LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API [IMetaDataImport](../metadata/imetadataimport-interface.md) i [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Takie metody mogą być napotkane przez program do zaprogramowania za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

Ten interfejs API może służyć do pobierania informacji o metodach dynamicznych, łącznie z przyjazną nazwą, jeśli jest dostępna.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo8, interfejs](icorprofilerinfo8-interface.md)
