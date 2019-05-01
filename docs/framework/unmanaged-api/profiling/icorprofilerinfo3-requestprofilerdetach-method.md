---
title: ICorProfilerInfo3::RequestProfilerDetach — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b04c0453d9ff8545f79f235e7d73095c55203e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049521"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach — Metoda
Powoduje, że środowisko uruchomieniowe, aby odłączyć profiler.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwExpectedCompletionMilliseconds`  
 [in] Czas w milisekundach, środowisko uruchomieniowe języka wspólnego (CLR) powinien odczekać przez sprawdzanie, czy jest bezpieczne zwolnić profiler.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Żądanie odłączenia jest prawidłowy, i procedury Odłącz jest teraz kontynuowane w innym wątku. Podczas odłączania zostanie całkowicie zakończona, `ProfilerDetachSucceeded` zdarzenie.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Wystąpił błąd profilera [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) spróbować uzyskać [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interfejs, który muszą implementować do obsługi operacji odłączania. Odłączanie nie podjęto próby.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Odłączenie jest niemożliwe, ponieważ program profilujący Ustaw flagi niezmienne przy uruchamianiu. Nie podjęto próby odłączenie; profiler jest nadal w pełni dołączony.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Odłączenie jest niemożliwe, ponieważ program profilujący używane Instrumentacji kod intermediate language (MSIL) firmy Microsoft lub wstawiono `enter` / `leave` punkty zaczepienia. Nie podjęto próby odłączenie; profiler jest nadal w pełni dołączony.<br /><br /> **Uwaga** Instrumentacji MSIL jest kod kod, który jest dostarczany przez profiler przy użyciu [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Środowisko wykonawcze nie została jeszcze zainicjowana w aplikacji zarządzanej. (Oznacza to, środowisko wykonawcze nie został w pełni załadowany.) Tego kodu błędu mogą być zwrócone zleconą odłączenie wewnątrz wywołania zwrotnego profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metody.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` została wywołana w chwili nieobsługiwany. Dzieje się tak Jeśli metoda jest wywoływana wątków zarządzanych, ale nie z poziomu [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody lub z poziomu [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody, które nie tolerują wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wykonywania procedury Odłącz, odłącz wątku (wątek służących do odłączenia profilera) od czasu do czasu sprawdza, czy wszystkie wątki zamknięciu programu profilującego kodu. Program profilujący powinien udostępniać oszacowanie, o ile to za pośrednictwem `dwExpectedCompletionMilliseconds` parametru. Dobrej wartość do wykorzystania jest typowy ilość czasu, program profilujący korzystało z wewnątrz każdego podane `ICorProfilerCallback*` metody; Metoda ta wartość nie powinna być części mniejszej od połowy maksymalną ilość czasu profiler oczekuje, że do wydania.  
  
 Używa wątku Odłącz `dwExpectedCompletionMilliseconds` zdecydować, jak długo do stanu uśpienia przed sprawdzeniem, czy kod wywołania zwrotnego profilera został zabrany ze stosów wszystkich. Chociaż szczegóły następującego algorytmu mogą ulec zmianie w przyszłych wersjach środowiska CLR, przedstawia on jeden ze sposobów `dwExpectedCompletionMilliseconds` mogą być używane podczas ustalania, kiedy jest bezpieczne zwolnić profiler. Wątek Odłącz najpierw zostanie uśpiony `dwExpectedCompletionMilliseconds` milisekund. Jeśli po aktywności ze stanu uśpienia, środowiska CLR stwierdzi, że jest nadal obecny kod wywołania zwrotnego profilera, wątek Odłącz przejścia w tryb uśpienia, obecnie dwa razy `dwExpectedCompletionMilliseconds` milisekund. Jeśli po aktywności z tego drugiego uśpienia, wątek Odłącz stwierdzi, że kod wywołania zwrotnego profilera nadal istnieje, zostanie uśpiony na 10 minut przed ponownym sprawdzeniem. Wątek Odłącz w dalszym ciągu Sprawdź ponownie co 10 minut.  
  
 Jeśli program profilujący Określa `dwExpectedCompletionMilliseconds` jako 0 (zero), środowisko CLR używa domyślnie wynosi 5000, co oznacza, że zostanie przeprowadzone sprawdzanie po 5 sekundach ponownie po 10 sekund, a następnie co 10 minut po tej dacie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
