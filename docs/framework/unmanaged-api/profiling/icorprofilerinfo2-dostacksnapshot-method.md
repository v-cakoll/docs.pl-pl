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
ms.openlocfilehash: b9a7142de01d818390b740a795f70a4606952780
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497377"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot — Metoda
Przegląda zarządzane ramki na stosie dla określonego wątku i wysyła informacje do profilera za pomocą wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `thread`  
 podczas Identyfikator wątku docelowego.  
  
 Przekazywanie wartości null w programie `thread` powoduje utworzenie migawki bieżącego wątku. W przypadku `ThreadID` przekazania innego wątku środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje ten wątek, wykonuje migawkę i wznawia działanie.  
  
 `callback`  
 podczas Wskaźnik do implementacji metody [StackSnapshotCallback —](stacksnapshotcallback-function.md) , który jest wywoływany przez środowisko CLR w celu udostępnienia profilera informacji na temat każdej zarządzanej ramki i każdego uruchomienia niezarządzanych ramek.  
  
 `StackSnapshotCallback`Metoda jest implementowana przez moduł zapisujący profilera.  
  
 `infoFlags`  
 podczas Wartość wyliczenia [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) , która określa ilość danych, które mają być przesyłane z powrotem dla każdej ramki przez `StackSnapshotCallback` .  
  
 `clientData`  
 podczas Wskaźnik do danych klienta, który jest przenoszona bezpośrednio do `StackSnapshotCallback` funkcji wywołania zwrotnego.  
  
 `context`  
 podczas Wskaźnik do `CONTEXT` struktury Win32, który jest używany do wypełniania przeszukiwania stosu. Struktura Win32 `CONTEXT` zawiera wartości rejestrów procesora i reprezentuje stan procesora CPU w określonym momencie.  
  
 Inicjator pozwala określić, gdzie zacząć przeszukiwanie stosu, jeśli góra stosu jest niezarządzanym kodem pomocnika. w przeciwnym razie inicjator zostanie zignorowany. Aby można było przeprowadzić przeprowadzenie asynchroniczne, należy podać inicjator. W przypadku przeprowadzania synchronicznego przechodzenia nie jest wymagany żaden inicjator.  
  
 `context`Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przeniesiona do `infoFlags` parametru.  
  
 `contextSize`  
 podczas Rozmiar `CONTEXT` struktury, do której odwołuje się `context` parametr.  
  
## <a name="remarks"></a>Uwagi  
 Przekazanie wartości null dla `thread` daje migawkę bieżącego wątku. Migawki mogą być podejmowane przez inne wątki tylko wtedy, gdy wątek docelowy jest wstrzymany w danym momencie.  
  
 Gdy profiler chce przeprowadzić stos, wywołuje `DoStackSnapshot` . Przed zwróceniem danych z tego wywołania przez środowisko CLR wywołuje `StackSnapshotCallback` kilka razy, raz dla każdej zarządzanej ramki (lub uruchamia niezarządzane ramki) na stosie. W przypadku napotkania ramek niezarządzanych należy zademonstrować je samodzielnie.  
  
 Kolejność, w której jest przeszukiwany stos, to odwracanie do sposobu wypychania ramek do stosu: liścia (ostatnio wypchnięcia), pierwsza klatka główna (pierwsza-wypchnięci) Ostatnia.  
  
 Aby uzyskać więcej informacji o tym, jak programować Profiler w celu przechodzenia do zarządzanych stosów, zobacz Samouczek dotyczący [stosu profilera w .NET Framework 2,0: podstawowe i poza](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10))nimi.  
  
 Przeszukiwanie stosu może być synchroniczne lub asynchroniczne, jak wyjaśniono w poniższych sekcjach.  
  
## <a name="synchronous-stack-walk"></a>Przeszukiwanie stosu synchronicznego  
 Synchroniczne przeszukiwanie stosu obejmuje przechodzenie stosu bieżącego wątku w odpowiedzi na wywołanie zwrotne. Nie wymaga użycia inicjatora ani wstrzymania.  
  
 Wywołanie synchroniczne należy wykonać, gdy, w odpowiedzi na środowisko CLR wywołuje jedną z metod [ICorProfilerCallback](icorprofilercallback-interface.md) (lub [ICorProfilerCallback2](icorprofilercallback2-interface.md)) profilera, wywoływanie, `DoStackSnapshot` Aby przeprowadzić stos bieżącego wątku. Jest to przydatne, gdy chcesz zobaczyć, jak wygląda stos przy użyciu powiadomienia, takiego jak [ICorProfilerCallback:: ObjectAllocated —](icorprofilercallback-objectallocated-method.md). Po prostu wywołaj `DoStackSnapshot` `ICorProfilerCallback` metodę, przekazując wartość null w `context` `thread` parametrach i.  
  
## <a name="asynchronous-stack-walk"></a>Przeszukiwanie stosu asynchronicznego  
 Asynchroniczne przeszukiwanie stosu pociąga za sobą stos innego wątku lub przechwycenie stosu bieżącego wątku, nie w odpowiedzi na wywołanie zwrotne, ale przez przejęcie wskaźnika instrukcji bieżącego wątku. Wykonywanie asynchroniczne jest wymagane, jeśli góra stosu jest niezarządzanym kodem, który nie jest częścią wywołania platformy (PInvoke) lub wywołaniem COM, ale kod pomocnika w samym środowisku CLR. Na przykład kod, który wykonuje Kompilowanie lub odzyskiwanie pamięci just-in-Time (JIT), jest kodem pomocnika.  
  
 Inicjator jest uzyskiwany przez bezpośrednie zawieszenie wątku docelowego i przeanalizowanie jego stosu do momentu znalezienia ramki zarządzanej znajdującej się najwyżej. Po wstrzymaniu wątku docelowego Pobierz bieżący kontekst rejestru wątku docelowego. Następnie ustal, czy kontekst rejestru wskazuje niezarządzany kod przez wywołanie [ICorProfilerInfo:: GetFunctionFromIP —](icorprofilerinfo-getfunctionfromip-method.md) — jeśli zwraca wartość `FunctionID` równą zero, jest to kod niezarządzany. Teraz przeprowadzisz stos do momentu osiągnięcia pierwszej zarządzanej ramki, a następnie obliczy Kontekst inicjatora na podstawie kontekstu rejestru dla tej ramki.  
  
 Wywołaj `DoStackSnapshot` z kontekstem inicjatora, aby rozpocząć przechodzenie przez stos asynchroniczny. Jeśli nie podasz inicjatora, program `DoStackSnapshot` może pominąć zarządzane ramki w górnej części stosu, co w efekcie spowoduje przeprowadzenie niekompletnego przeszukiwania stosu. W przypadku dostarczania inicjatora należy wskazać kod wygenerowany przez KOMPILATOR lub Generator obrazu natywnego (Ngen. exe). w przeciwnym razie `DoStackSnapshot` zwraca kod błędu, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Asynchroniczne przechodzenia stosu mogą łatwo prowadzić do zakleszczenii lub naruszeń praw dostępu, chyba że są przestrzegane następujące wytyczne:  
  
- W przypadku bezpośredniego zawieszenia wątków należy pamiętać, że tylko wątek, który nigdy nie uruchamia kodu zarządzanego może zawiesić inny wątek.  
  
- Zawsze blokuj do wywołania zwrotnego [ICorProfilerCallback:: ThreadDestroyed —](icorprofilercallback-threaddestroyed-method.md) , dopóki nie zostanie wykonane przechodzenie stosu.  
  
- Nie przechowuj blokady, gdy profiler wywołuje funkcję CLR, która może wyzwolić wyrzucanie elementów bezużytecznych. Oznacza to, że nie należy blokować blokady, jeśli wątek będący właścicielem może wykonać wywołanie wyzwalające wyrzucanie elementów bezużytecznych.  
  
 Istnieje również ryzyko zakleszczenia w przypadku wywołania `DoStackSnapshot` z wątku utworzonego przez profiler, aby można było wykonać stos oddzielnego wątku docelowego. Przy pierwszym utworzeniu wątku zostaną wprowadzone pewne `ICorProfilerInfo*` metody (w tym: `DoStackSnapshot` ), środowisko CLR wykona inicjalizację specyficzną dla środowiska CLR dla tego wątku. Jeśli profiler wstrzymał wątek docelowy, którego stos próbujesz wykonać, a w przypadku tego wątku docelowego nastąpiło zablokowanie niezbędne do wykonania tego wątku, zakleszczenie zostanie wykonane. Aby uniknąć tego zakleszczenia, należy nawiązać początkowe wywołanie `DoStackSnapshot` z wątku utworzonego przez profiler w celu przeprowadzenia oddzielnego wątku docelowego, ale nie należy najpierw wstrzymać wątku docelowego. To początkowe wywołanie zapewnia, że inicjalizacja poszczególnych wątków może zakończyć się bez zakleszczenia. Jeśli program `DoStackSnapshot` zakończy się pomyślnie i zgłosi co najmniej jedną ramkę, będzie on bezpieczny dla wątku utworzonego przez profiler, aby zawiesić każdy wątek docelowy i wywołanie w `DoStackSnapshot` celu przeprowadzenia stosu tego wątku docelowego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
