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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049443"
---
# <a name="icorprofilerinfo5-interface"></a>Interfejs ICorProfilerInfo5
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Podklasa klasy [icorprofilerinfo4 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , udostępnia metody do użycia przez profilery kodu do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR) do kontrolowania, monitorowanie zdarzeń.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|Pobiera bieżący kategorie zdarzeń, dla których program profilujący chce otrzymywać powiadomienia, ze środowiska CLR.|  
|[SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|Ustawia wartość, która określa typy zdarzeń, dla których program profilujący chce otrzymywać powiadomienia o zdarzeniach, ze środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Metody dostępne dla tego interfejsu są przeznaczone do zastąpienia [icorprofilerinfo::geteventmask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) i [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
