---
title: Interfejs ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861726"
---
# <a name="icorprofilerinfo5-interface"></a>Interfejs ICorProfilerInfo5
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Podklasa elementu [ICorProfilerInfo4](icorprofilerinfo4-interface.md) , która dostarcza metody do użycia przez program Code profilowas do komunikowania się ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu kontrolowania monitorowania zdarzeń.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetEventMask2, metoda](icorprofilerinfo5-geteventmask2-method.md)|Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu CLR.|  
|[SetEventMask2, metoda](icorprofilerinfo5-seteventmask2-method.md)|Ustawia wartość określającą typy zdarzeń, dla których profiler chce odbierać powiadomienia o zdarzeniach z środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Metody dostępne w tym interfejsie zastępują metody [ICorProfilerInfo:: GetEventMask —](icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
