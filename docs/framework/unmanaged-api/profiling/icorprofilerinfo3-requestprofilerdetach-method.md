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
ms.openlocfilehash: e69a15d70b8f1b9e271571be92f1f6717a9f196c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach — Metoda
Powoduje, że środowisko uruchomieniowe można odłączyć profilera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwExpectedCompletionMilliseconds`  
 [in] Czas (w milisekundach), środowisko uruchomieniowe języka wspólnego (CLR) ma odczekać przed sprawdzanie, czy jest bezpieczne zwolnić profilera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Odłącz żądanie jest prawidłowe, i procedury odłączeń jest teraz kontynuowane w innym wątku. W przypadku odłączenia zostanie całkowicie zakończona, `ProfilerDetachSucceeded` zdarzenie.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Wystąpił błąd [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) podejmować dla [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interfejs, który musi implementować do obsługi operacji odłączania. Odłączanie nie podjęto próby.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Oderwania jest niemożliwe, ponieważ profiler Ustaw flagi niezmienne podczas uruchamiania. Nie podjęto próby oderwania; profiler nadal pełni jest dołączony.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Oderwania jest niemożliwe, ponieważ profiler używane zinstrumentowane kod języka pośredniego (MSIL) firmy Microsoft lub wstawionego `enter` / `leave` punkty zaczepienia. Nie podjęto próby oderwania; profiler nadal pełni jest dołączony.<br /><br /> **Uwaga** Zinstrumentowane MSIL jest kod jest kod, który odbywa się przy użyciu profilera [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Środowisko uruchomieniowe nie zostały jeszcze zainicjowane w zarządzanej aplikacji. (To znaczy środowiska uruchomieniowego nie został całkowicie załadowany.) Tego kodu błędu mogą być zwrócone zleconą oderwania wewnątrz wywołania zwrotnego profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metody.|  
|WYNIK CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` została wywołana w czasie nieobsługiwany. Dzieje się tak, jeśli metoda jest wywoływana w wątku zarządzanego, ale nie za pomocą [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody lub z poziomu [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody, które nie tolerują wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Uwagi  
 Podczas wykonywania procedury detach detach wątku (Wątek utworzony specjalnie z myślą o odłączanie profilera) od czasu do czasu sprawdza, czy wszystkie wątki zamknięciu kodu profilera. Profilera powinien podać prognozę, jak długo powinien zostać za pośrednictwem `dwExpectedCompletionMilliseconds` parametru. Dobrym wartości do użycia to typowe ilość czasu profilera zużywa wewnątrz żadnej podanej `ICorProfilerCallback*` metody; ta wartość nie powinna być mniejsza niż połowy maksymalną ilość czasu profilera oczekuje poświęcić.  
  
 Wątek detach używa `dwExpectedCompletionMilliseconds` decyzji o tym, jak długo do stanu uśpienia przed sprawdzeniem, czy kod wywołania zwrotnego profilera ma zostały zdjęte ze stosu Wyłącz wszystkie stosy. Mimo że szczegóły następującego algorytmu mogą ulec zmianie w przyszłych wersjach środowiska CLR, zastosowano jeden ze sposobów `dwExpectedCompletionMilliseconds` może być używana podczas ustalania, kiedy jest bezpieczne zwolnić profilera. Wątek Odłącz najpierw zostanie uśpiony na `dwExpectedCompletionMilliseconds` milisekund. Jeśli po aktywności ze stanu uśpienia, CLR stwierdzi, że profiler wywołania zwrotnego kodu jest nadal się tam, odłącz wątek jest w stanie uśpienia ponownie, czas dwa razy `dwExpectedCompletionMilliseconds` milisekund. Jeśli po aktywności z tego drugiego uśpienia, odłącz wątku stwierdzi, że profiler wywołania zwrotnego kodu nadal się tam, zostanie uśpiony na 10 minut przed ponownym sprawdzeniem. Odłącz wątku w dalszym ciągu ponownie co 10 minut.  
  
 Jeśli określa profilera `dwExpectedCompletionMilliseconds` jako 0 (zero), korzysta z wartości domyślnej 5000, co oznacza, że zostanie przeprowadzone sprawdzanie po 5 sekund, ponownie za 10 sekund, a następnie co 10 minut, następnie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
