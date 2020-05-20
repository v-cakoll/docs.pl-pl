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
ms.openlocfilehash: dbcf9230a953069d311c3908aa3ed21fcfd5075c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420269"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach — Metoda
Nakazuje programowi uruchomieniowemu odłączenie profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwExpectedCompletionMilliseconds`  
 podczas Czas (w milisekundach), przez który środowisko uruchomieniowe języka wspólnego (CLR) powinien czekać przed sprawdzeniem, czy można bezpiecznie zwolnić Profiler.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Żądanie odłączenia jest prawidłowe i Procedura odłączania jest teraz kontynuowana w innym wątku. Gdy odłączenie jest w pełni kompletne, `ProfilerDetachSucceeded` zostanie wygenerowane zdarzenie.|  
|E_CORPROF_E_CALLBACK3_REQUIRED|Profiler nie może wykonać operacji [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) dla interfejsu [ICorProfilerCallback3](icorprofilercallback3-interface.md) , który musi zostać zaimplementowany, aby obsługiwał operację odłączania. Nie podjęto próby odłączenia.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Odłączenie jest niemożliwe, ponieważ Profiler ustawił niezmienne flagi podczas uruchamiania. Nie podjęto próby odłączenia; Profiler jest nadal w pełni dołączony.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Odłączenie jest niemożliwe, ponieważ Profiler używa kodu pośredniego języka Microsoft (MSIL) lub wstawianych `enter` / `leave` punktów zaczepienia. Nie podjęto próby odłączenia; Profiler jest nadal w pełni dołączony.<br /><br /> **Uwaga** Instrumentacja MSIL to kod, który jest dostarczany przez profiler przy użyciu metody [SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) .|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Środowisko uruchomieniowe nie zostało jeszcze zainicjowane w aplikacji zarządzanej. (Oznacza to, że środowisko uruchomieniowe nie zostało w pełni załadowane). Ten kod błędu może zostać zwrócony w przypadku zażądania odłączenia wewnątrz metody [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego profilera.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach`został wywołany w nieobsługiwanym czasie. Dzieje się tak, jeśli metoda jest wywoływana w wątku zarządzanym, ale nie z metody [ICorProfilerCallback](icorprofilercallback-interface.md) lub z metody [ICorProfilerCallback](icorprofilercallback-interface.md) , która nie może tolerować wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Uwagi  
 Podczas procedury odłączania wątek odłączania (wątek utworzony w celu odłączenia profilera) sporadycznie sprawdza, czy wszystkie wątki zakończyły kod profilera. Profiler powinien zapewnić przybliżony czas, jaki powinien upłynąć przez `dwExpectedCompletionMilliseconds` parametr. Dobrą wartością do użycia jest typowa ilość czasu, przez który Profiler spędza w ramach danej `ICorProfilerCallback*` metody; ta wartość nie powinna być mniejsza niż połowa maksymalnego czasu oczekiwania przez profiler.  
  
 Wątek odłączania używa `dwExpectedCompletionMilliseconds` do określenia czasu uśpienia przed sprawdzeniem, czy kod wywołania zwrotnego profilera został zdjęte poza wszystkie stosy. Mimo że szczegółowe informacje o następującym algorytmie mogą ulec zmianie w przyszłych wydaniach środowiska CLR, można użyć jednego ze sposobów, `dwExpectedCompletionMilliseconds` Aby określić, kiedy jest bezpieczne do zwolnienia profilera. Wątek odłączania jest najpierw uśpiony przez `dwExpectedCompletionMilliseconds` milisekundy. Jeśli po przejściu z trybu uśpienia środowisko CLR stwierdzi, że kod wywołania zwrotnego profilera nadal jest obecny, ten wątek odłączania będzie się powtarzał, tym razem przez dwa razy w `dwExpectedCompletionMilliseconds` milisekundach. Jeśli po przejściu z tego drugiego stanu uśpienia wątek odłączania odnajdzie kod wywołania zwrotnego profilera, który jest nadal obecny, zostanie on oduśpiony przez 10 minut przed ponownym sprawdzeniem. Wątek odłączania kontynuuje sprawdzanie ponownie co 10 minut.  
  
 Jeśli profiler określa `dwExpectedCompletionMilliseconds` jako 0 (zero), środowisko CLR używa domyślnej wartości 5000, co oznacza, że przeprowadzi sprawdzanie po 5 sekundach, ponownie po upływie 10 sekund, a następnie co 10 minut później.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
