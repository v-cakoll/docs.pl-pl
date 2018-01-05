---
title: "ICorProfilerInfo4::InitializeCurrentThread — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread — Metoda
Inicjuje bieżący wątek klienta z wyprzedzeniem kolejnych profilera, który wywołania interfejsu API w tym samym wątku, aby uniknąć tego zakleszczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Firma Microsoft zaleca, aby wywołać `InitializeCurrentThread` w którymkolwiek wątku, który będzie dzwonić profiler interfejsu API, gdy są zawieszone wątków. Ta metoda jest zwykle używana przez profilowania próbkowania, które utworzyć własne wątku do wywołania [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) przedstawiono metodę w celu stosu podczas docelowy wątek jest zawieszony. Wywołując `InitializeCurrentThread` po po profilera najpierw tworzy wątku próbkowania, profilery można zapewnić, inicjowanie tego wątku opóźnieniem, które wykonywania innych podczas pierwszego wywołania do środowiska CLR `DoStackSnapshot` może teraz wystąpić bezpiecznie kiedy są nie ma innych wątków zawieszone.  
  
> [!NOTE]
>  `InitializeCurrentThread`nie inicjowania z wyprzedzeniem, aby zakończyć zadania wykonuj blokad, które mogą zakleszczenie. Wywołanie `InitializeCurrentThread` tylko wtedy, gdy nie ma żadnych zawieszonych wątków.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
