---
title: ICorProfilerInfo2::DoStackSnapshot — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c65e48595f2b49abe06e649898649d76a0668a0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678311"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot — Metoda
Przedstawia zarządzanych ramek na stosie dla określonego wątku, a następnie wysyła informacje do profilera za pośrednictwem wywołania zwrotnego.  
  
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
 [in] Identyfikator docelowego wątku.  
  
 Przekazanie wartości null w `thread` daje migawkę bieżącego wątku. Jeśli `ThreadID` z innym wątku jest przekazywany, środowisko uruchomieniowe języka wspólnego (CLR) zawiesza wątek, wykonuje migawkę i zostanie wznowione.  
  
 `callback`  
 [in] Wskaźnik do implementacji [stacksnapshotcallback —](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) metody, która jest wywoływana przez środowisko CLR zapewnienie profiler informacji na temat każdej zarządzanej ramki i każde uruchomienie niezarządzanych ramek.  
  
 `StackSnapshotCallback` Metoda jest implementowana przez moduł zapisujący profilera.  
  
 `infoFlags`  
 [in] Wartość [cor_prf_snapshot_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) wyliczenia, który określa ilość danych do przekazania ponownie dla każdej ramki przez `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Wskaźnik do danych klienta, która jest przekazywana bezpośrednio do `StackSnapshotCallback` funkcji wywołania zwrotnego.  
  
 `context`  
 [in] Wskaźnik do systemu Win32 `CONTEXT` struktury, która jest używana w celu umieszczenia przeszukiwania stosu. Win32 `CONTEXT` struktura zawiera wartości rejestrów Procesora i przedstawia stan Procesora w danym momencie w czasie.  
  
 Inicjatora pomaga CLR, określić, jak zacząć przeszukiwania stosu, jeśli kod niezarządzany pomocnika; Szczyt stosu w przeciwnym razie inicjatora jest ignorowany. Inicjator musi zostać dostarczony dla asynchronicznego przeszukiwania. Jeśli przeprowadzasz synchroniczne przeszukiwania Inicjator nie jest konieczne.  
  
 `context` Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT przekazano `infoFlags` parametru.  
  
 `contextSize`  
 [in] Rozmiar `CONTEXT` struktury, która odwołuje się do niej `context` parametru.  
  
## <a name="remarks"></a>Uwagi  
 Przekazanie wartości null dla `thread` daje migawkę bieżącego wątku. Migawki mogą być wykonywane inne wątków, tylko wtedy, gdy wątek docelowy jest zawieszony w czasie.  
  
 Gdy profiler chce zapoznać się ze stosu, wywołuje `DoStackSnapshot`. Zanim CLR zwraca z wywołania, wywoływanych przez nią Twojej `StackSnapshotCallback` kilka razy, raz dla każdego zarządzanego ramki (lub uruchom ramek niezarządzanych) na stosie. Po napotkaniu ramki niezarządzanych, użytkownik musi prowadzą użytkownika je samodzielnie.  
  
 Kolejność, w której zostaje przeprowadzony stosu jest odwrotnością sposobu ramki są wypychane na stosie: ostatnia liści (wypychania przez ostatnie) po pierwsze, głównym (wypychania pierwszy) klatka.  
  
 Aby uzyskać więcej informacji na temat sposobu programowania programu profilującego do przejścia przez stosy zarządzane, zobacz [Profiler stosu zalet w programie .NET Framework 2.0: podstawy i](https://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Przeszukiwania stosu może być synchroniczna lub asynchroniczna, zgodnie z opisem w poniższych sekcjach.  
  
## <a name="synchronous-stack-walk"></a>Synchroniczne stosów  
 Synchroniczne stosów obejmuje zalet stosu bieżący wątek w odpowiedzi na wywołanie zwrotne. Nie wymaga rozmieszczania lub zawieszenie.  
  
 Wprowadzone przez synchroniczny wywołania, gdy w odpowiedzi na środowisko CLR, wywołując jedną Twój program profilujący [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (lub [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) metody, należy wywołać `DoStackSnapshot` przeprowadzenie stos Bieżący wątek. Jest to przydatne, jeśli chcesz zobaczyć, jak stos wygląda na powiadomienie takich jak [icorprofilercallback::objectallocated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Po prostu Wywołaj `DoStackSnapshot` z poziomu usługi `ICorProfilerCallback` metody, przekazując wartość null w `context` i `thread` parametrów.  
  
## <a name="asynchronous-stack-walk"></a>Asynchroniczne stosów  
 Asynchroniczne stosów pociąga za sobą zalet stosu innym wątku lub zalet stosu bieżący wątek nie ma w odpowiedzi na wywołanie zwrotne, ale przez przejmującą adresy wskaźnik instrukcji bieżącego wątku. Asynchroniczne przeszukiwania wymaga inicjatora, jeśli kod niezarządzany, który nie jest częścią platformy Szczyt stosu wywołania (funkcja PInvoke) lub wywołania modelu COM, ale kod pomocniczy w środowisku CLR, sam. Na przykład kod, który obsługuje just-in-time (JIT) kompilacja lub wyrzucania elementów kolekcji jest kod pomocnika.  
  
 Uzyskaj inicjator bezpośrednio wstrzymując wątek docelowy i zalet swój stos samodzielnie, dopóki nie znajdziesz najwyższy zarządzane ramki. Po elemencie docelowym wątek jest zawieszony, pobieranie bieżącego kontekstu rejestru wątek docelowy. Następnie należy określić, czy kontekst rejestru wskazuje do kodu niezarządzanego, wywołując [icorprofilerinfo::getfunctionfromip —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — Jeśli zwróci ona `FunctionID` równa zero, ramki jest kod niezarządzany. Teraz Przeprowadź stosu, aż do pierwszej ramki zarządzanej, a następnie obliczyć kontekstu inicjatora, na podstawie kontekstu rejestru dla tej ramki.  
  
 Wywołaj `DoStackSnapshot` z kontekstu inicjatora do rozpoczęcia asynchronicznego stosów. Jeśli nie podasz inicjatora `DoStackSnapshot` może pominąć zarządzanych ramek w górnej części stosu i w związku z tym, zapewni niekompletne stosów. Jeśli podasz inicjator musi wskazywać kompilowanego dokładnie na czas lub Native Image Generator (Ngen.exe)-wygenerowanego kodu; w przeciwnym razie `DoStackSnapshot` zwraca kod błędu, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Przeszukiwania stosu asynchronicznego łatwo może spowodować zakleszczenia lub dostępu do naruszenia, chyba, że należy przestrzegać następujących wytycznych:  
  
-   Po wstrzymaniu bezpośrednio wątków, należy pamiętać, że tylko wątku, który nigdy nie uruchomił kodu zarządzanego można wstrzymać inny wątek.  
  
-   Zawsze należy zablokować w swojej [icorprofilercallback::threaddestroyed —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) wywołania zwrotnego do czasu ukończenia przeszukiwania stosu dla wątku.  
  
-   Blokady nie są przechowywane, gdy Twój program profilujący wywołania do funkcji CLR, która może wyzwalać wyrzucania elementów bezużytecznych. Oznacza to nie posiadają blokadę, jeśli wątek będący właścicielem może spowodować wywołanie, która wyzwala wyrzucanie elementów bezużytecznych.  
  
 Istnieje również ryzyko zakleszczenia Jeśli wywołasz `DoStackSnapshot` z wątku, który został utworzony swojego programu profilującego, dzięki czemu możesz zapoznać się z stosu wątku oddzielne docelowe. Wprowadza wątek został utworzony po raz pierwszy, niektóre `ICorProfilerInfo*` metody (w tym `DoStackSnapshot`), środowisko CLR będzie wykonywać inicjacje na wątek, specyficzne dla środowiska CLR dla tego wątku. Jeśli Twój program profilujący został wstrzymany wątek docelowy stosu, którego chcesz, aby zapoznać się z, a ten wątek docelowy stało się z właścicielem blokady wymagany do wykonania tego wątku inicjowania, nastąpi zakleszczenia. Aby uniknąć tego zakleszczenia, należy początkowej wywołać `DoStackSnapshot` z wątek utworzone przez program profilujący przeprowadzenie wątek docelowy oddzielny, ale nie zawiesić wątek docelowy, najpierw. To wywołanie początkowej zapewnia, wykonać inicjowania na wątek bez zakleszczenia. Jeśli `DoStackSnapshot` zakończy się pomyślnie i zgłasza co najmniej jedną ramką po tym momencie są one bezpieczne dla tego wątku utworzone przez program profilujący do wstrzymania dowolnego wątek docelowy i wywołanie `DoStackSnapshot` przeprowadzenie stosu ten wątek docelowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** } CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
