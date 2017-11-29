---
title: "ICorProfilerInfo2::DoStackSnapshot — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.DoStackSnapshot
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type: apiref
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a210fc0c1984ee9bc77114ba30c3287ae43b169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot — Metoda
Przeprowadzi zarządzanych ramek na stosie dla określonego wątku i wysyła informacje do profilera za pośrednictwem wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `thread`  
 [in] Identyfikator wątku docelowej.  
  
 Przekazywanie wartości null w `thread` daje migawkę bieżącego wątku. Jeśli `ThreadID` z innego wątku jest przekazywany, środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje wątek, wykonuje migawkę i zostanie wznowione.  
  
 `callback`  
 [in] Wskaźnik do wykonania [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) metodę, która jest wywoływana przez środowisko CLR zapewnienie profilera informacji na temat każdej ramce zarządzanych i każdym uruchomieniu niezarządzane ramki.  
  
 `StackSnapshotCallback` Metody jest implementowany przez twórcę profilera.  
  
 `infoFlags`  
 [in] Wartość [cor_prf_snapshot_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) wyliczenia, która określa ilość danych do przekazania wstecz dla każdej ramce przez `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Wskaźnik do danych klienta, który jest przekazywana bezpośrednio do `StackSnapshotCallback` funkcja wywołania zwrotnego.  
  
 `context`  
 [in] Wskaźnik do Win32 `CONTEXT` struktury, która jest używana jako zalążek przeszukiwania stosu. Win32 `CONTEXT` struktury zawiera wartości rejestrów Procesora i przedstawia stan Procesora w danym momencie w czasie.  
  
 Inicjatora pomaga CLR określenie miejsca rozpocząć przeszukiwania stosu ze szczytu stosu jest kodu niezarządzanego pomocnika; w przeciwnym razie wartość inicjatora jest ignorowana. Inicjator musi zostać dostarczona dla asynchronicznego przeszukiwania. Inicjator nie jest niezbędne, jeśli przeprowadzasz synchroniczne przeszukiwania.  
  
 `context` Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przekazana `infoFlags` parametru.  
  
 `contextSize`  
 [in] Rozmiar `CONTEXT` struktury, która odwołuje się do niego `context` parametru.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywanie wartości null dla `thread` daje migawkę bieżącego wątku. Migawki mogą być wykonywane inne wątki tylko wtedy, gdy wątek docelowy jest zawieszony w czasie.  
  
 Gdy profilera chce przeprowadzić stosu, wywołuje `DoStackSnapshot`. Przed CLR zwraca z tego wywołania, wywołuje Twojej `StackSnapshotCallback` kilka razy, raz dla każdego zarządzanego ramki (lub uruchom niezarządzane ramki) na stosie. Gdy wystąpią niezarządzane ramki, użytkownik musi Przeprowadź je samodzielnie.  
  
 Kolejność, w którym jest udał stosu jest odwrotnej jak zostały przekazane ramek na stosie: ostatniego typu liść (wypychana ostatnich) po pierwsze, głównego (wypychana pierwszej) klatka.  
  
 Aby uzyskać więcej informacji na temat programu profiler do przeszukania zarządzane stosy, zobacz [profilera stosu przejście w .NET Framework 2.0: podstawy i poza](http://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Przeszukiwania stosu można synchroniczna lub asynchroniczna, zgodnie z objaśnieniem w poniższych sekcjach.  
  
## <a name="synchronous-stack-walk"></a>Synchroniczne stosów  
 Synchroniczne stosów obejmuje przejście stosu bieżącego wątku w odpowiedzi na wywołanie zwrotne. Nie wymaga wstępne wypełnianie lub zawieszenie.  
  
 Wprowadzeniu synchroniczne wywołania, gdy w odpowiedzi na CLR wywołaniem programu profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (lub [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) wywołania metody, `DoStackSnapshot` przeprowadzenie stos Bieżący wątek. Jest to przydatne, jeśli chcesz zobaczyć stos jak wygląda na powiadomienie o takich jak [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Należy wywołać `DoStackSnapshot` z poziomu programu `ICorProfilerCallback` metody przekazywanie wartości null w `context` i `thread` parametrów.  
  
## <a name="asynchronous-stack-walk"></a>Asynchroniczne stosów  
 Asynchroniczne stosów pociąga za sobą przejście stosu przez inny wątek lub przejście stosu bieżący wątek nie znajduje się w odpowiedzi na wywołanie zwrotne, ale przez przejmującą wskaźnik instrukcji bieżącego wątku. Asynchroniczne przeszukiwania wymaga inicjatora w przypadku ze szczytu stosu kodu niezarządzanego, który nie wchodzi w skład platformy wywołania (PInvoke) lub wywołania modelu COM, ale kod pomocniczy samego środowiska CLR. Na przykład kod, który obsługuje just in time (JIT) kompilowanie lub odzyskiwanie kolekcji jest kod pomocniczy.  
  
 Uzyskaj inicjator bezpośrednio wstrzymując wątek docelowy i przejście swój stos samodzielnie, do momentu znalezienia najwyższy węzeł zarządzany ramki. Po elemencie docelowym wątek jest zawieszony, Pobierz wątek docelowy bieżącego kontekstu rejestru. Następnie należy określić, czy kontekst rejestru punktów do kodu niezarządzanego przez wywołanie metody [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — Jeśli zwróci ona `FunctionID` równa zero, ramka to kodu niezarządzanego. Teraz Przeprowadź stosu, aż do pierwszej ramki zarządzane, a następnie obliczyć kontekstu inicjatora na podstawie kontekstu rejestru dla tej ramki.  
  
 Wywołanie `DoStackSnapshot` z kontekstu inicjatora zacząć przeszukiwania stosu asynchronicznego. Jeśli nie podasz inicjatora `DoStackSnapshot` może pominąć ramki zarządzane w górnej części stosu, a w rezultacie zapewni stosów niekompletne. Jeśli podasz inicjator musi wskazywać Generator obrazu natywnego lub kompilacji JIT (Ngen.exe)-wygenerowanego kodu; w przeciwnym razie `DoStackSnapshot` zwraca kod niepowodzenia CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Przeszukiwań stosu asynchroniczne łatwo może spowodować zakleszczenie lub dostęp do naruszenia, chyba że przestrzegać następujących wytycznych:  
  
-   Po wstrzymaniu bezpośrednio wątków, należy pamiętać, że tylko wątku, który nigdy nie został uruchomiony z kodu zarządzanego można wstrzymać inny wątek.  
  
-   Zawsze należy zablokować w Twojej [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) wywołania zwrotnego do czasu ukończenia stosów dla wątku.  
  
-   Nie przytrzymując blokady profilera wywołano funkcji CLR, które mogą wyzwalać wyrzucania elementów bezużytecznych. Oznacza to, że nie posiadają blokady Jeśli wątek będący właścicielem może uniemożliwić wywołanie, które wyzwala wyrzucania elementów bezużytecznych.  
  
 Istnieje również ryzyko zakleszczenia połączeń `DoStackSnapshot` z wątku, który profilera został utworzony, dzięki czemu można przeprowadzić stosu wątku oddzielne docelowej. Wprowadza wątek został utworzony po raz pierwszy, niektóre `ICorProfilerInfo*` metod (w tym `DoStackSnapshot`), środowisko CLR będzie wykonywać na wątek, inicjowania CLR specyficzne wątek. Jeśli profilera wstrzymał wątek docelowy stosu, którego chcesz przeprowadzić, a wątek docelowy stało się właścicielem blokady niezbędne do wykonywania tego inicjowania dla każdego wątku, nastąpi zakleszczenie. Aby uniknąć tego zakleszczenia, należy początkowej wywołanie `DoStackSnapshot` z Twojej wątku utworzonych przez profiler do przeszukania oddzielnej target wątku, ale nie wstrzymania wątku docelowy, najpierw. To wywołanie początkowej zapewnia, że inicjowania dla każdego wątku można wykonać bez zakleszczenia. Jeśli `DoStackSnapshot` zakończy się pomyślnie, a następnie raportuje co najmniej jedną ramkę, po tym momencie będzie bezpieczne dla tego wątku utworzonych przez profiler wstrzymania wątek docelowy, a wywołania `DoStackSnapshot` przeprowadzenie stosu wątek docelowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
