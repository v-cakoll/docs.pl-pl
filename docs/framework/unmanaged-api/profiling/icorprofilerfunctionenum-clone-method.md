---
title: ICorProfilerFunctionEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ded15608337d040ab58cb5be45deac4711668ac3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576177"
---
# <a name="icorprofilerfunctionenumclone-method"></a>ICorProfilerFunctionEnum::Clone — Metoda
Pobiera wskaźnik interfejsu do kopii tego [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interfejsu. Kopię moduł wyliczający zachowuje swój własny stan wyliczenia, niezależnie od tego modułu wyliczającego. Jednak pozycja kursora początkowa kopia jest taki sam jak ten moduł wyliczający bieżącej pozycji kursora.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerFunctionEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
