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
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447707"
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|Środowisko uruchomieniowe jest zawieszone z nieokreślonego powodu.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Środowisko uruchomieniowe jest zawieszone w celu obsługi żądania wyrzucania elementów bezużytecznych.<br /><br /> Wywołania zwrotne dotyczące wyrzucania elementów bezużytecznych są wykonywane między elementami wywołania zwrotne [ICorProfilerCallback:: RuntimeSuspendFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i [ICorProfilerCallback:: RuntimeResumeStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) .|  
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

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
