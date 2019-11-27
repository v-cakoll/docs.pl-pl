---
title: ICorProfilerCallback::Shutdown — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446945"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown — Metoda
Powiadamia program profilujący, że aplikacja jest zamykana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod profilera nie może bezpiecznie wywołać metod interfejsu [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) po wywołaniu metody `Shutdown`. Wszystkie wywołania metod `ICorProfilerInfo` powodują niezdefiniowane zachowanie po powrocie metody `Shutdown`. Po zamknięciu mogą nadal występować pewne niezmienne zdarzenia. Profiler powinien zwrócić uwagę natychmiast po wystąpieniu tego problemu.  
  
 Metoda `Shutdown` zostanie wywołana tylko wtedy, gdy zarządzana aplikacja, która jest profilowana, została uruchomiona jako kod zarządzany (oznacza to, że początkowa ramka na stosie procesów jest zarządzana). Jeśli aplikacja została uruchomiona jako kod niezarządzany, ale później przeskoczy do kodu zarządzanego, tworząc wystąpienie środowiska uruchomieniowego języka wspólnego (CLR), a następnie `Shutdown` nie zostanie wywołana. W takich przypadkach Profiler powinien znajdować się w swojej bibliotece `DllMain` procedura, która używa wartości DLL_PROCESS_DETACH do zwolnienia wszelkich zasobów i wykonywania czyszczenia danych, takich jak opróżnianie śladów na dysk i tak dalej.  
  
 Ogólnie rzecz biorąc, profiler musi poradzić sobie z nieoczekiwanymi zamknięciami. Na przykład proces może być zatrzymany przez metodę Win32's `TerminateProcess` (zadeklarowany w Winbase. h). W innych przypadkach środowisko CLR zatrzyma pewne zarządzane wątki (wątki w tle) bez dostarczania do nich uporządkowanych komunikatów o zniszczeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
