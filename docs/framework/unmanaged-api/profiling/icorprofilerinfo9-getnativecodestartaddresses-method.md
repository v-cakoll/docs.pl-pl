---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868281"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses, Metoda

Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>Parametry

- `functionId`

  \[in) identyfikator funkcji, której powinny zostać zwrócone adresy początkowe kodu natywnego.

- `reJitId`

  \[] tożsamość funkcji ponownie skompilowanej JIT.

- `cCodeStartAddresses`

  \[] maksymalny rozmiar tablicy `codeStartAddresses`.

- `pcCodeStartAddresses`

  \[out] Liczba dostępnych adresów.

- `codeStartAddresses`

  \[out] tablica `UINT_PTR`, z których każdy jest adresem początkowym dla określonej funkcji.

## <a name="remarks"></a>Uwagi

Gdy kompilacja warstwowa jest włączona, funkcja może mieć więcej niż jedną treść kodu natywnego.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo9, interfejs](icorprofilerinfo9-interface.md)
