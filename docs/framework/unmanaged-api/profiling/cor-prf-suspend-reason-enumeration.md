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
ms.openlocfilehash: 2f4382c7fa85008de9e67ad21c467402bae4ac90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451285"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON — Wyliczenie
Wskazuje przyczynę zawieszenia środowiska uruchomieniowego.  
  
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
|`COR_PRF_FIELD_SUSPEND_OTHER`|Środowisko wykonawcze jest wstrzymana z nieokreślonego powodu.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Środowisko uruchomieniowe zostanie zawieszony w celu obsługi żądania kolekcji pamięci.<br /><br /> Wywołania zwrotne dotyczące kolekcji pamięci, występują między [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) i [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) wywołań zwrotnych.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Środowisko wykonawcze jest wstrzymana, aby `AppDomain` może zostać wyłączony.<br /><br /> Gdy środowisko wykonawcze jest wstrzymane, środowiska uruchomieniowego określi wątków, które znajdują się w `AppDomain` czyli Trwa zamykanie i ustaw je, aby przerwać, gdy są one. Istnieją nie `AppDomain`-określonych wywołań zwrotnych podczas tego zawieszenia.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Środowisko uruchomieniowe został wstrzymany, dzięki czemu kod pitching może wystąpić.<br /><br /> Kod pitching ensues, tylko gdy przy użyciu kompilatora just in time (JIT) jest aktywny z kodu pitching włączone. Kod pitching wywołania zwrotne występują między `ICorProfilerCallback::RuntimeSuspendFinished` i `ICorProfilerCallback::RuntimeResumeStarted` wywołań zwrotnych. **Uwaga:** CLR JIT nie osoba funkcji w programie .NET Framework w wersji 2.0, dlatego ta wartość nie jest używana w 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Środowisko uruchomieniowe zostało zawieszone, dzięki czemu można zamknąć. Musi ona zawiesić wszystkie wątki do ukończenia tej operacji.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Zawieszone środowiska uruchomieniowego w trakcie debugowania.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Środowisko uruchomieniowe został wstrzymany, aby przygotować się do wyrzucania elementów bezużytecznych.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Środowisko wykonawcze jest wstrzymana na potrzeby ponownej kompilacji JIT.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wątki środowiska uruchomieniowego znajdujących się za pomocą kodu niezarządzanego mogą nadal działać do chwili próbują ponownie wprowadzić środowiska uruchomieniowego w takim przypadku one będą również zawieszone, dopóki nie zostanie wznowione środowiska uruchomieniowego. Dotyczy to również nowy wątków, które należy wprowadzić środowiska uruchomieniowego. Wszystkie wątki wewnątrz środowiska uruchomieniowego są zawieszone natychmiast, gdy są one w kodzie przerywania albo zadawane wstrzymania po osiągnięciu przerywania kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
