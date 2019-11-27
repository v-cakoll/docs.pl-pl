---
title: ICorProfilerInfo4::InitializeCurrentThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 39882a554f9d47040bef00ff320d15b56abea533
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445717"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread — Metoda
Inicjuje bieżący wątek przed kolejnymi wywołaniami interfejsu API profilera w tym samym wątku, aby można było uniknąć zakleszczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Zalecamy wywołanie `InitializeCurrentThread` w dowolnym wątku, który wywoła interfejs API profilera, gdy są zawieszone wątki. Ta metoda jest zwykle używana przez pliki do próbkowania, które tworzą własny wątek wywołujący [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodę, aby wykonać przeszukiwanie stosu, gdy wątek docelowy jest zawieszony. Wywołując `InitializeCurrentThread` raz, gdy profiler najpierw tworzy wątek próbkowania, mogą one zagwarantować, że inicjalizacja każdego wątku środowiska CLR w przeciwnym razie będzie działać podczas pierwszego wywołania do `DoStackSnapshot` może być bezpiecznie wykonywana, gdy nie zostaną wstrzymane żadne inne wątki.  
  
> [!NOTE]
> `InitializeCurrentThread` wykonuje inicjalizację, aby zakończyć zadania, które mają blokadę i mogą być zakleszczenie. Wywołaj `InitializeCurrentThread` tylko wtedy, gdy nie ma żadnych zawieszonych wątków.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
