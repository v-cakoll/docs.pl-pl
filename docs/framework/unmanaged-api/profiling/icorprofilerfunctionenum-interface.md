---
title: ICorProfilerFunctionEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e77ec9de198b673bb3b5fc4dad3cd1b0316f07c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092074"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum — Interfejs
Udostępnia metody do sekwencyjnie iteracji przez kolekcję funkcji środowiska uruchomieniowego języka wspólnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Pobiera wskaźnik interfejsu do kopii tego `ICorProfilerFunctionEnum` interfejsu.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Pobiera liczbę funkcji, które zostały załadowane do aplikacji lub Wymuś ładowany przez program profilujący.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Pobiera określoną liczbę funkcji ciągłego z sekwencyjną kolekcją funkcji, zaczynając od modułu wyliczającego bieżąca pozycja w sekwencji.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Przenosi kursor modułu wyliczającego do pozycji początkowej sekwencji.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak, aby określoną liczbę elementów są pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerFunctionEnum` Interfejs jest moduł wyliczający. Umożliwia odbiorcy tablicy do ściągnięcia elementów od nadawcy szybkością, która jest odpowiednia dla odbiorcy. Innymi słowy odbiornik jest w stanie jawnie sterowania przepływem elementów tablicy, tym samym unikając problemów związanych z przekazywania dużych tablic jako parametrów metody.  
  
 `ICorProfilerFunctionEnum` Wylicza za pośrednictwem funkcji, które zostały już skompilowane JIT, ale nie obejmuje funkcje, które są ładowane z obrazy natywne generowane przez program Ngen.exe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
