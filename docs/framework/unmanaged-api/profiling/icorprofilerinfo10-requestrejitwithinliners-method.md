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
ms.openlocfilehash: 00bfc9fc21ed39226fd21c4096305c254d73ee11
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665727"
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

#### <a name="parameters"></a>Parametry

`dwRejitFlags` \
podczas Maska bitów [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).

`cFunctions` \
podczas Liczba funkcji, które mają zostać ponownie skompilowane.

`moduleIds` \
podczas Określa część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane. `moduleId`

`methodIds` \
podczas Określa część par (`module`, `methodDef`), które identyfikują funkcje, które mają być ponownie skompilowane. `methodId`

## <a name="remarks"></a>Uwagi

[RequestReJIT —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) nie wykonuje żadnych śledzonych metod. Profiler powinien zablokować tworzenie i śledzenie i wywoływać `RequestReJIT` wszystkie elementy, aby upewnić się, że każde wystąpienie metody wbudowanej zostało ReJITted. Stanowi to problem z ReJIT po dołączeniu, ponieważ Profiler nie jest obecny do monitorowania tworzenia konspektu. Ta metoda może być wywoływana w celu zagwarantowania, że pełny zestaw elementów ReJITted również będzie się znajdować.

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Nagłówki** CorProf. idl, CorProf. h

**Biblioteki** CorGuids.lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo10, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
