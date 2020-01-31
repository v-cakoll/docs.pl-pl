---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 5822136eb1a7f582bcfae901a99775950e586198
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863182"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners, Metoda

ReJITs wymagane metody, a także wszystkie wbudowane metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>Parametry

- `dwRejitFlags`

  \[w) — Maska bitów [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[] liczba funkcji, które mają zostać ponownie skompilowane.

- `moduleIds`

  \[in] określa `moduleId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.

- `methodIds`

  \[in] określa `methodId` część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane.

## <a name="remarks"></a>Uwagi

[RequestReJIT —](icorprofilerinfo4-requestrejit-method.md) nie wykonuje żadnych śledzonych metod. Profiler powinien zablokować tworzenie i śledzenie i wywoływać `RequestReJIT` dla wszystkich elementów, aby upewnić się, że każde wystąpienie metody wbudowanej zostało ReJITted. Stanowi to problem z ReJIT po dołączeniu, ponieważ Profiler nie jest obecny do monitorowania tworzenia konspektu. Ta metoda może być wywoływana w celu zagwarantowania, że pełny zestaw elementów ReJITted również będzie się znajdować.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo10, interfejs](icorprofilerinfo10-interface.md)
