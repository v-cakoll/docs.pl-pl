---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 74300a12d000565a63cd7ea862c759d47b87bbe1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665695"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a>ICorProfilerInfo10:: SuspendRuntime, Metoda

Wstrzymuje środowisko uruchomieniowe bez wykonywania operacji GC.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Nagłówki** CorProf. idl, CorProf. h

**Biblioteki** CorGuids.lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo10, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
