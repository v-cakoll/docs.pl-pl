---
title: Ograniczone regiony wykonania
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0561ff5212fd6bc4e9015bea8da1d1082dd027e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046696"
---
# <a name="constrained-execution-regions"></a>Ograniczone regiony wykonania
Ograniczony region wykonywania (CER) jest częścią mechanizmu tworzenia niezawodnego kodu zarządzanego. CER definiuje obszar, w którym środowisko uruchomieniowe języka wspólnego (CLR) jest ograniczone od zgłaszania wyjątków poza pasmem, które mogłyby uniemożliwić wykonywanie kodu w obszarze w całości. W tym regionie kod użytkownika jest ograniczony do wykonywania kodu, który mógłby spowodować Przerzucanie wyjątków poza pasmem. `catch` `finally` `fault` Metoda musi bezpośrednio `try` poprzedzać blok i znaczniki, i bloki jako ograniczone regiony wykonywania. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Po oznaczeniu jako regionu ograniczonego kod musi wywoływać inny kod tylko z silną umową niezawodności, a kod nie powinien przydzielać ani wykonywać połączeń wirtualnych do nieprzygotowanych lub wiarygodnych metod, chyba że kod jest przygotowany do obsługi błędów. Wątek CLR opóźnia przerwanie dla kodu, który jest wykonywany w CER.  
  
 Ograniczone regiony wykonywania są używane w różnych formularzach środowiska CLR oprócz `try` bloku z adnotacjami, szczególnie dla kluczowych finalizatorów wykonywanych w klasach pochodnych <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> klasy <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> i kodu wykonywanych przy użyciu metody.  
  
## <a name="cer-advance-preparation"></a>Zaawansowane przygotowanie do CER  
 Środowisko CLR przygotuje CERs z wyprzedzeniem, aby uniknąć braku pamięci. Przygotowywanie z wyprzedzeniem jest wymagane, aby środowisko CLR nie powodowało braku pamięci w czasie kompilacji just in Time lub typu ładowania.  
  
 Deweloper jest zobowiązany do wskazania, że region kodu jest CER:  
  
- Region i metody CER najwyższego poziomu w grafie <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> pełnego wywołania z zastosowanym atrybutem są przygotowywane z wyprzedzeniem. Tylko gwarancje stanu <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>lub. <xref:System.Runtime.ConstrainedExecution.Cer.Success> <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>  
  
- Nie można wykonać przygotowania zaawansowania dla wywołań, które nie mogą być określane statycznie, takie jak wysyłanie wirtualne. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> Użyj metody w takich przypadkach. W przypadku korzystania <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> z metody <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> atrybut powinien zostać zastosowany do kodu czyszczącego.  
  
## <a name="constraints"></a>Ograniczenia  
 Użytkownicy są ograniczeniami w typie kodu, który można napisać w CER. Kod nie może spowodować wyjątku poza pasmem, na przykład może wynikać z następujących operacji:  
  
- Jawna alokacja.  
  
- Opakowanie.  
  
- Uzyskiwanie blokady.  
  
- Wywoływanie nieprzygotowanych metod praktycznie.  
  
- Wywoływanie metod z słabym lub nieistniejącym kontraktem niezawodności.  
  
 W .NET Framework w wersji 2,0 te ograniczenia są wskazówkami. Diagnostyka jest świadczona za poorednictwem narzędzi do analizy kodu.  
  
## <a name="reliability-contracts"></a>Kontrakty niezawodności  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Jest atrybutem niestandardowym, który dokumentuje gwarancje niezawodności i stan uszkodzenia danej metody.  
  
### <a name="reliability-guarantees"></a>Gwarancje niezawodności  
 Gwarancje niezawodności, reprezentowane <xref:System.Runtime.ConstrainedExecution.Cer> przez wartości wyliczenia, wskazują stopień niezawodności danej metody:  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. W przypadku wyjątkowych warunków Metoda może zakończyć się niepowodzeniem. W tym przypadku Metoda raportuje z powrotem do metody wywołującej, czy zakończyła się powodzeniem, czy niepowodzeniem. Metoda musi być zawarta w CER, aby można było zgłosić wartość zwracaną.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.None>. Metoda, typ lub zestaw nie ma koncepcji CER i najprawdopodobniej nie jest to bezpieczne do wywołania w programie CER bez znacznego ograniczenia uszkodzenia stanu. Nie wykorzystuje ona gwarancji CER. Oznacza to następujące kwestie:  
  
    1. W wyjątkowych warunkach Metoda może zakończyć się niepowodzeniem.  
  
    2. Metoda może lub nie zgłasza, że zakończyła się niepowodzeniem.  
  
    3. Metoda nie jest zapisywana, aby używać CER, najbardziej prawdopodobną przyczyną.  
  
    4. Jeśli metoda, typ lub zestaw nie został jawnie zidentyfikowany do sukcesu, jest on niejawnie zidentyfikowany jako <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.Success>. W wyjątkowych warunkach Metoda ma gwarancję pomyślnego zakończenia. Aby osiągnąć ten poziom niezawodności, należy zawsze skonstruować plik CER wokół metody, która jest wywoływana, nawet gdy jest wywoływana z poziomu regionu innego niż CER. Metoda zakończyła się powodzeniem, jeśli osiąga to zamierzone, chociaż sukces może być przeglądany w sposób subiektywny. Na przykład liczba oznaczania z `ReliabilityContractAttribute(Cer.Success)` oznacza, że gdy jest uruchamiany w ramach cer, zawsze zwraca liczbę elementów <xref:System.Collections.ArrayList> w i nigdy nie pozostawia pól wewnętrznych w stanie nieokreślonym.  <xref:System.Threading.Interlocked.CompareExchange%2A> Jednak metoda jest oznaczona jako sukces, a zrozumienie, że powodzenie może oznaczać, że wartość nie może zostać zastąpiona nową wartością ze względu na sytuację wyścigu.  Kluczowym punktem jest to, że metoda zachowuje się w sposób, w jaki jest zachowywać się, a kod CER nie musi być zapisany, aby oczekiwać dowolnego nietypowego zachowania poza zakresem prawidłowym, ale kod niezawodny.  
  
### <a name="corruption-levels"></a>Poziomy uszkodzeń  
 Poziomy uszkodzeń reprezentowane przez <xref:System.Runtime.ConstrainedExecution.Consistency> wartości wyliczenia, wskazują, ile stanu może być uszkodzony w danym środowisku:  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. W wyjątkowych warunkach środowisko uruchomieniowe języka wspólnego (CLR) nie gwarantuje spójności stanu w bieżącej domenie aplikacji.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. W ramach wyjątkowych warunków Metoda ma ograniczyć uszkodzenie stanu do bieżącego wystąpienia.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>W warunkach wyjątkowych środowisko CLR nie gwarantuje spójności stanu. oznacza to, że warunek może uszkodzić proces.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. W warunkach wyjątkowych Metoda ma gwarancję nieuszkodzenia stanu.  
  
## <a name="reliability-trycatchfinally"></a>Niezawodność try/catch/finally  
 Niezawodność `try/catch/finally` to mechanizm obsługi wyjątków o tym samym poziomie gwarancji przewidywalności jako wersja niezarządzana. `catch/finally` Blok jest CER. Metody w bloku wymagają przygotowania z wyprzedzeniem i muszą być noninterruptible.  
  
 W .NET Framework w wersji 2,0 kod informuje środowisko uruchomieniowe, że próbka jest niezawodna, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> wywołując bezpośrednio poprzedzające blok try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>jest członkiem <xref:System.Runtime.CompilerServices.RuntimeHelpers>klasy obsługi kompilatora. Wywoływanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezpośrednio w oczekiwany sposób za jego dostępność za poorednictwem kompilatorów.  
  
## <a name="noninterruptible-regions"></a>Regiony Noninterruptible  
 Region noninterruptible grupuje zestaw instrukcji do CER.  
  
 W .NET Framework wersja 2,0, oczekująca dostępność za pomocą obsługi kompilatora, kod użytkownika tworzy regiony inne niż przerywania z niezawodną instrukcją try/catch/finally, która zawiera pusty blok try/ <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> catch poprzedzony wywołaniem metody.  
  
## <a name="critical-finalizer-object"></a>Krytyczny obiekt finalizatora  
 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> Gwarantuje, że wyrzucanie elementów bezużytecznych wykona finalizator. Po przydzieleniu, finalizator i jego Graf wywołań są przygotowane z wyprzedzeniem. Metoda finalizatora jest wykonywana przez program CER i musi przestrzegać wszystkich ograniczeń dotyczących CERs i finalizatorów.  
  
 Wszystkie typy dziedziczenia z <xref:System.Runtime.InteropServices.SafeHandle> i <xref:System.Runtime.InteropServices.CriticalHandle> są gwarantowane, że finalizator jest wykonywany w ramach CER. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Zaimplementuj <xref:System.Runtime.InteropServices.SafeHandle> w klasach pochodnych, aby wykonać dowolny kod, który jest wymagany do zwolnienia dojścia.  
  
## <a name="code-not-permitted-in-cers"></a>Kod nie jest dozwolony w CERs  
 Następujące operacje są niedozwolone w CERs:  
  
- Jawne alokacje.  
  
- Uzyskiwanie blokady.  
  
- Opakowanie.  
  
- Dostęp do tablicy wielowymiarowej.  
  
- Wywołania metody poprzez odbicie.  
  
- <xref:System.Threading.Monitor.Enter%2A>lub <xref:System.IO.FileStream.Lock%2A>.  
  
- Sprawdzanie zabezpieczeń. Nie wykonuj wymagań, tylko w przypadku żądań linków.  
  
- <xref:System.Reflection.Emit.OpCodes.Isinst>i <xref:System.Reflection.Emit.OpCodes.Castclass> dla obiektów com i serwerów proxy  
  
- Pobieranie lub Ustawianie pól na przezroczystym serwerze proxy.  
  
- Serializacji.  
  
- Wskaźniki funkcji i delegatów.  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze rozwiązania dotyczące niezawodności](reliability-best-practices.md)
