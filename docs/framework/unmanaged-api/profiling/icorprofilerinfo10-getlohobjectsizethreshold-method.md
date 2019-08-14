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
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973754"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold, Metoda
  
 Pobiera wartość wartości progowej skonfigurowanej sterty dużych obiektów (LOH).   
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a>Parametry  
 `pThreshold` \
 określoną Próg sterty dużego obiektu w bajtach.
  
## <a name="remarks"></a>Uwagi  
 Obiekty większe niż próg sterty dużego obiektu zostaną przydzieloną na stercie dużego obiektu. Począwszy od platformy .NET Core 3,0 próg sterty dużego obiektu jest konfigurowalny, `pThreshold` będzie zawierać aktywny rozmiar progu sterty dużego obiektu w bajtach.

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo10, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

