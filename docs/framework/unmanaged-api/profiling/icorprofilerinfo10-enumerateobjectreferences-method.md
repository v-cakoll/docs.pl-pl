---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ac193b6b78434245b8f11a4f627b4e1992feb8a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661277"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10:: EnumerateObjectReferences, Metoda

Podanym identyfikatorem ObjectID, wywołaniem zwrotnym i clientData, wylicza każde odwołanie do obiektu (jeśli istnieje).

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a>Parametry

`objectId` \
podczas Obiekt, na którym mają zostać wyliczone odwołania.

`callback` \
podczas Funkcja, która będzie wywoływana z odwołaniami dla obiektu.

`clientData` \
podczas Dane dostarczone przez `callback` Profiler do przekazania do funkcji.

## <a name="remarks"></a>Uwagi

Metoda jest podobna do ObjectReferences —, z tą różnicą, że przeprowadza odwołania na żądanie dla profilera zamiast wstępnie przydzielić tablicę do przechowywania odwołań. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) `EnumerateObjectReferences`

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Nagłówki** CorProf. idl, CorProf. h

**Biblioteki** CorGuids.lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo10, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
