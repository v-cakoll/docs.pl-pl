---
title: 'ICorProfilerInfo10:: iszamarzniętobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661222"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: iszamarzniętobject — Metoda

Przy użyciu identyfikatora ObjectID określa, czy obiekt znajduje się w segmencie tylko do odczytu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a>Parametry

`objectId` \
podczas Obiekt do sprawdzenia.

`pbFrozen` \
określoną Wskazuje `BOOL` , czy obiekt znajduje się w segmencie tylko do odczytu.

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Nagłówki** CorProf. idl, CorProf. h

**Biblioteki** CorGuids.lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo10, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
