---
title: ICorProfilerModuleEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 2713fa90240cb0bf41f455b6ed65d76c568a2cf8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868268"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum — Interfejs
Dostarcza metody sekwencyjnie iteracji przez kolekcję modułów ładowanych przez aplikację lub profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](icorprofilermoduleenum-clone-method.md)|Pobiera wskaźnik interfejsu do kopii tego interfejsu `ICorProfilerModuleEnum`.|  
|[GetCount, metoda](icorprofilermoduleenum-getcount-method.md)|Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.|  
|[Next, metoda](icorprofilermoduleenum-next-method.md)|Pobiera określoną liczbę modułów ciągłego z kolekcji sekwencyjnej obiektów, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.|  
|[Reset, metoda](icorprofilermoduleenum-reset-method.md)|Przenosi kursor modułu wyliczającego do początkowego położenia sekwencji.|  
|[Skip, metoda](icorprofilermoduleenum-skip-method.md)|Przesuwa pozycję kursora modułu wyliczającego tak, aby określona liczba elementów została pominięta.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorProfilerModuleEnum` jest modułem wyliczającym. Umożliwia odbiorcom tablicy ściąganie elementów od nadawcy według stawki, która jest odpowiednia dla odbiornika. Innymi słowy, odbiorca może jawnie kontrolować przepływ elementów tablicy, co pozwala uniknąć problemów związanych z przekazywaniem dużych tablic jako parametrów metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [EnumModules, metoda](icorprofilerinfo3-enummodules-method.md)
