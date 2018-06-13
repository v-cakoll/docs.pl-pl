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
ms.openlocfilehash: a1e55c7e6deff3928e69861541aa1a924dac263f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455065"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum — Interfejs
Udostępnia metody sekwencyjnie iterowania po kolekcji funkcji środowiska CLR.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Pobiera wskaźnika interfejsu kopię `ICorProfilerFunctionEnum` interfejsu.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Pobiera liczbę funkcji, które zostały załadowane do aplikacji lub Wymuś załadowanych przez profiler.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Pobiera określoną liczbę funkcji ciągłego z sekwencyjną kolekcją funkcji, zaczynając od modułu wyliczającego bieżącej pozycji w sekwencji.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Przesuwa kursor modułu wyliczającego pozycji początkowej sekwencji.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Przesuwa kursor modułu wyliczającego z jego bieżącym położeniu tak, aby określoną liczbę elementów są pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerFunctionEnum` Interfejs jest moduł wyliczający. Umożliwia odbiorcy tablicy do ściągania elementów od nadawcy szybkością, który jest odpowiedni dla odbiornika. Innymi słowy odbiorca jest w stanie jawnie sterowanie przepływem elementów tablicy, zapobiegając problemów związanych z przekazywanie dużych tablic jako parametrów metody.  
  
 `ICorProfilerFunctionEnum` Wylicza za pośrednictwem funkcji, które zostały już kompilacji JIT, ale nie zawiera funkcje, które są ładowane z obrazów macierzystych wygenerowane z Ngen.exe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumJITedFunctions, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
