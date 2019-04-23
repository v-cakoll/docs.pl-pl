---
title: ICorProfilerObjectEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14e8086532eff5dba6883575cc2daf447a32343a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182367"
---
# <a name="icorprofilerobjectenumclone-method"></a>ICorProfilerObjectEnum::Clone — Metoda
Pobiera wskaźnik interfejsu do kopii tego [icorprofilerobjectenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię `ICorProfilerObjectEnum` interfejsu. Zachowuje swój własny stan wyliczenia, niezależnie od niej. Jednak pozycja kursora początkowa kopia będzie taki sam jak ten moduł wyliczający bieżącej pozycji kursora.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerObjectEnum, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
