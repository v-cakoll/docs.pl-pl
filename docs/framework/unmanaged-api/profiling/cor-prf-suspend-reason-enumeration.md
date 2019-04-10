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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21533b5173bcd91d0c944fbde4eafc9817de8315
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220061"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON — Wyliczenie
Wskazuje powód, że środowisko uruchomieniowe została wstrzymana.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`COR_PRF_FIELD_SUSPEND_OTHER`|Środowisko uruchomieniowe jest zawieszona z nieokreślonego powodu.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Środowisko uruchomieniowe jest zawieszona do obsłużenia żądania kolekcji wyrzucania elementów.<br /><br /> Wywołania zwrotne dotyczące kolekcji wyrzucania elementów wystąpić między [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i [icorprofilercallback::runtimeresumestarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Środowisko uruchomieniowe jest wstrzymana, aby `AppDomain` może zostać wyłączony.<br /><br /> Gdy środowisko uruchomieniowe jest wstrzymane, środowisko uruchomieniowe określi, które wątki są `AppDomain` czyli jest zamknięta i je przerwać po ich wznowić. Istnieją nie `AppDomain`-określonych wywołania zwrotne podczas tego zawieszenia.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Środowisko uruchomieniowe jest wstrzymana, tak, aby kod pitching mogą wystąpić.<br /><br /> Kod pitching ensues, tylko gdy kompilator just-in-time (JIT) jest aktywny za pomocą kodu pitching włączone. Kod pitching wywołania zwrotne wystąpić między `ICorProfilerCallback::RuntimeSuspendFinished` i `ICorProfilerCallback::RuntimeResumeStarted` wywołania zwrotne. **Uwaga:**  CLR JIT nie zawodowcom funkcje w wersji 2.0, .NET Framework, dlatego ta wartość nie jest używany w wersji 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Środowisko uruchomieniowe jest wstrzymana, dzięki czemu można zamknąć. Należy je zawiesić wszystkich wątków do wykonania danej operacji.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Środowisko uruchomieniowe jest zawieszony w procesie debugowania.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Środowisko uruchomieniowe jest zawieszony, aby przygotować się do wyrzucania elementów bezużytecznych.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Środowisko uruchomieniowe jest zawieszona na potrzeby ponownej kompilacji JIT.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wątki środowiska uruchomieniowego, które są w niezarządzanym kodzie są dozwolone, aby kontynuować, dopóki użytkownik podejmie próbę ponownego wprowadzania środowiska uruchomieniowego, w tym momencie one będą również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego. Dotyczy to również nowe wątki, które wprowadzać środowiska uruchomieniowego. Wszystkie wątki w ramach środowiska uruchomieniowego są zawieszone natychmiast, jeśli są one w kodzie są albo monit wstrzymać, gdy osiągną oni limit przerywania kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — Wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
