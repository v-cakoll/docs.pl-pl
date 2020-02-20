---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7a0f6f6bea5bc919ebfe9c9acc3b02a31eaa7cd0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452217"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold, Metoda

Pobiera wartość wartości progowej skonfigurowanej sterty dużych obiektów (LOH).

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>Parametry

- `pThreshold`

  \[out] próg sterty dużego obiektu w bajtach.

## <a name="remarks"></a>Uwagi

Obiekty większe niż próg sterty dużego obiektu zostaną przydzieloną na stercie dużego obiektu. Począwszy od platformy .NET Core 3,0, można skonfigurować próg sterty dużego obiektu, `pThreshold` będzie zawierać aktywny rozmiar progu sterty dużego obiektu w bajtach.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Zobacz też

- [ICorProfilerInfo10, interfejs](icorprofilerinfo10-interface.md)
