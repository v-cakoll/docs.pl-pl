---
title: COR_PRF_SUSPEND_REASON — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: 1036ecbdb735b95c0ad6897c1545e3bd8cb6c3a9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867077"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>COR_PRF_SUSPEND_REASON — Wyliczenie
Wskazuje przyczynę zawieszenia środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|Środowisko uruchomieniowe jest zawieszone z nieokreślonego powodu.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Środowisko uruchomieniowe jest zawieszone w celu obsługi żądania wyrzucania elementów bezużytecznych.<br /><br /> Wywołania zwrotne dotyczące wyrzucania elementów bezużytecznych są wykonywane między elementami wywołania zwrotne [ICorProfilerCallback:: RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md) i [ICorProfilerCallback:: RuntimeResumeStarted —](icorprofilercallback-runtimeresumestarted-method.md) .|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Środowisko uruchomieniowe jest zawieszone, aby można było wyłączyć `AppDomain`.<br /><br /> Gdy środowisko uruchomieniowe jest wstrzymane, środowisko uruchomieniowe określi, które wątki znajdują się w `AppDomain`, które są zamykane, i ustawia je do przerwania po wznowieniu. W tym zawieszeniu nie ma żadnych wywołań zwrotnych specyficznych dla `AppDomain`.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Środowisko uruchomieniowe jest zawieszone, aby można było następować w kodzie.<br /><br /> Pochylenia kodu nastąpią, gdy kompilator just in Time (JIT) jest aktywny z włączonym postawem kodu. Wywołania zwrotne dotyczące pochylenia kodu są wykonywane między `ICorProfilerCallback::RuntimeSuspendFinished` i `ICorProfilerCallback::RuntimeResumeStarted` wywołania zwrotne. **Uwaga:**  Środowisko CLR JIT nie ma skoku funkcji w .NET Framework w wersji 2,0, więc ta wartość nie jest używana w 2,0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Środowisko uruchomieniowe jest zawieszone, aby można je było wyłączyć. Musi zawiesić wszystkie wątki, aby ukończyć operację.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Środowisko uruchomieniowe jest zawieszone na potrzeby debugowania w procesie.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Środowisko uruchomieniowe jest zawieszone, aby przygotować się do wyrzucania elementów bezużytecznych.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Środowisko uruchomieniowe jest zawieszone na potrzeby ponownej kompilacji JIT.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wątki środowiska uruchomieniowego, które znajdują się w kodzie niezarządzanym, mogą kontynuować działanie, dopóki nie spróbują ponownie wprowadzić środowiska uruchomieniowego. w tym momencie zostaną one zawieszone do momentu wznowienia działania środowiska uruchomieniowego. Dotyczy to również nowych wątków, które wprowadzają środowisko uruchomieniowe. Wszystkie wątki w środowisku uruchomieniowym są zawieszane natychmiast, jeśli znajdują się w kodzie przerywania lub zażądają zawieszenia, gdy docierają do kodu przerywania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
