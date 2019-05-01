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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fd0900e61c57d105439d83430284dc8634d2a1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000509"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread — Metoda
Inicjuje bieżący wątek ewentualnej profilującym kolejnych wywołań interfejsu API w tym samym wątku, dzięki czemu można uniknąć tego zakleszczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Firma Microsoft zaleca wywołanie `InitializeCurrentThread` dotyczące dowolnego wątku, który będzie wybierany program profilujący interfejsu API, gdy istnieją wstrzymane wątki. Ta metoda jest zwykle używana przez profilowania próbkowania, tworzonych z własnych wątków do wywoływania [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) przedstawia metodę w celu stosu, gdy wątek docelowy jest wstrzymane. Przez wywołanie metody `InitializeCurrentThread` po kiedy profiler najpierw tworzy wątek próbkowania, profilery zagwarantować, że inicjowanie wątku z opóźnieniem, w przeciwnym razie wykona środowiska CLR Podczas pierwszego wywołania `DoStackSnapshot` teraz możliwe bezpiecznie kiedy są nie ma innych wątków zawieszone.  
  
> [!NOTE]
>  `InitializeCurrentThread` wykonuje inicjowanie z wyprzedzeniem, aby zakończyć zadania, które były blokad i może zakleszczenie. Wywołaj `InitializeCurrentThread` tylko wtedy, gdy nie istnieją wątki zawieszone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
