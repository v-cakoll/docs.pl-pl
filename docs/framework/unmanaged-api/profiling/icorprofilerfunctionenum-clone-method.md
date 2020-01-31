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
ms.openlocfilehash: 2faa7185202b46e77e501d69bb471391a7c6eb68
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864625"
---
# <a name="icorprofilerfunctionenumclone-method"></a>ICorProfilerFunctionEnum::Clone — Metoda
Pobiera wskaźnik interfejsu do kopii tego interfejsu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 określoną Wskaźnik do wskaźnika interfejsu, który z kolei wskazuje na kopię tego interfejsu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) . Kopia modułu wyliczającego utrzymuje swój własny stan wyliczenia niezależnie od tego modułu wyliczającego. Jednak początkowa pozycja kursora kopii jest taka sama jak pozycja bieżącego kursora tego modułu wyliczającego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionEnum, interfejs](icorprofilerfunctionenum-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
