---
title: Ograniczone regiony wykonania
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 719e24652ea40d601523e32ecbdb58ce5d4fa645
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616597"
---
# <a name="constrained-execution-regions"></a>Ograniczone regiony wykonania
Region ograniczonego wykonania (CER) jest częścią mechanizm służący do tworzenia niezawodnego kodu zarządzanego. CER definiuje obszar, w której środowisko uruchomieniowe języka wspólnego (CLR) jest ograniczony z zgłaszanie wyjątków poza pasmem, które mogłyby uniemożliwić wykonanie w całości kodu w obszarze. W tym regionie kod użytkownika jest ograniczony z wykonywania kodu, które mogłyby spowodować zgłaszanie wyjątków poza pasmem. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Metody musi bezpośrednio poprzedzać `try` bloku i znaczniki `catch`, `finally`, i `fault` bloków jako ograniczone regiony wykonania. Gdy oznaczony jako ograniczone region, kod tylko należy wywołać inny kod z kontrakty niezawodności silne, a kod nie może przydzielić lub wykonywać wywołania wirtualnego nieprzygotowane lub zawodnej metody, chyba że kod jest przygotowana do obsługi błędów. Przerywa wątku opóźnienia środowiska CLR dla kodu, który jest wykonywany w CER.  
  
 Ograniczone regiony wykonania są używane w różnych formularzach w środowisku CLR, oprócz adnotacjami `try` zablokować, szczególnie krytyczne finalizatory wykonywanie w klasach pochodzących od <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> klasy i kod, posługując się <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody.  
  
## <a name="cer-advance-preparation"></a>Przygotowań CER  
 Środowisko CLR przygotowuje CERs z wyprzedzeniem, aby uniknąć warunków braku pamięci. Przygotowań jest wymagane, aby środowisko CLR nie powoduje, że stan braku pamięci podczas ładowania kompilacji lub typu just-in-time.  
  
 Deweloper jest wymagana do wskazania, że region kodu jest CER:  
  
- Najwyższego poziomu region CER i wykresie pełną wywołania metod, które mają <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> zastosowany są przygotowywane z wyprzedzeniem. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Można tylko stan gwarancji <xref:System.Runtime.ConstrainedExecution.Cer.Success> lub <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
- Nie można wykonać przygotowań do wywołań, które statycznie nieokreślonym, takie jak wirtualne wysyłania. Użyj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody w tych przypadkach. Korzystając z <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> atrybut powinien zostać zastosowany na kod czyszczenia.  
  
## <a name="constraints"></a>Ograniczenia  
 Użytkownicy są ograniczone w typu kodu, które mogą zapisywać w CER. Kod nie może spowodować wyjątek poza pasmem, takich jak może wynikać z następujących czynności:  
  
- Jawne alokacji.  
  
- Pakowanie.  
  
- Pobieranie blokady.  
  
- Wywoływanie metody nieprzygotowane praktycznie.  
  
- Wywoływanie metod za pomocą kontraktu niezawodność słabych lub nie istnieje.  
  
 W .NET Framework w wersji 2.0 te ograniczenia są wskazówki. Diagnostyka są realizowane za pośrednictwem narzędzi analizy kodu.  
  
## <a name="reliability-contracts"></a>Kontrakty niezawodności  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Jest atrybutem niestandardowym, która dokumentuje gwarancje niezawodności i stanu uszkodzenia danej metody.  
  
### <a name="reliability-guarantees"></a>Gwarancje niezawodności  
 Gwarancje niezawodności, reprezentowane przez <xref:System.Runtime.ConstrainedExecution.Cer> wartości wyliczenia, wskazać stopnia niezawodności danej metody:  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. W wyjątkowych warunkach metoda może zakończyć się niepowodzeniem. W tym przypadku metoda raportuje ją do wywoływania metody czy zakończyła się powodzeniem lub nie powiodło się. Metoda musi być zawarty w CER, aby upewnić się, że zwracana wartość może raportować.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.None>. Metoda, typ lub zespół nie używa koncepcji CER i najprawdopodobniej nie można bezpiecznie wywołać w ramach CER bez znaczne ograniczenie ze stanu uszkodzenia. Go nie korzystaj z gwarancje CER. Oznacza to, że:  
  
    1. W wyjątkowych warunkach metoda może zakończyć się niepowodzeniem.  
  
    2. Metoda może być lub może nie raportować, że jej nie powiodło się.  
  
    3. Metoda nie jest zapisywany do użycia CER, najbardziej prawdopodobnym scenariuszem.  
  
    4. Jeśli metoda, typ lub zestawu nie jest jawnie zidentyfikowana zakończyło się sukcesem, niejawnie jest identyfikowany jako <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.Success>. W wyjątkowych warunkach metoda jest gwarantowane zakończyło się sukcesem. Aby osiągają ten poziom niezawodności należy zawsze utworzyć CER wokół metodę, która jest wywoływana, nawet gdy jest wywoływana z w obrębie regionu innego niż CER. Metoda jest powodzenia, jeśli rozwiązanie przeznaczenie, mimo że sukces, które mogą być wyświetlane subiektywnie. Na przykład oznaczenie liczba z `ReliabilityContractAttribute(Cer.Success)` oznacza, że po uruchomieniu w obszarze CER zawsze zwraca liczbę elementów w <xref:System.Collections.ArrayList> i nigdy nie można pozostawić pola wewnętrzne w stanie nieokreślony.  Jednak <xref:System.Threading.Interlocked.CompareExchange%2A> metoda jest oznaczona jako Powodzenie, przy założeniu, że sukces może oznaczać, że wartość mogły nie zostać zastąpione nowymi wartościami z powodu sytuacji wyścigu.  Kluczowym punktem jest metoda działa w taki sposób, który jest udokumentowany zachowanie i CER kodu nie jest konieczne można zapisać oczekiwać wszelkie nietypowe zachowanie poza wyglądałyby jaki kod poprawna, ale nieprzewidywalne.  
  
### <a name="corruption-levels"></a>Uszkodzenie poziomy  
 Poziomy uszkodzeniem, reprezentowane przez <xref:System.Runtime.ConstrainedExecution.Consistency> wartości wyliczenia wskazuje, ile stanu może być uszkodzona w danym środowisku:  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. W wyjątkowych warunkach środowisko uruchomieniowe języka wspólnego (CLR) nie udziela żadnych gwarancji dotyczących spójności stanu w bieżącej domenie aplikacji.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. W wyjątkowych warunkach metody jest gwarantowane, aby ograniczyć uszkodzenia stanu do bieżącego wystąpienia.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, W wyjątkowych warunkach, środowisko CLR nie udziela żadnych gwarancji dotyczących stanu spójności; oznacza to, że ten stan może spowodować uszkodzenie procesu.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. W wyjątkowych warunkach metody daje gwarancję doprowadzić do uszkodzenia.  
  
## <a name="reliability-trycatchfinally"></a>Niezawodność try/catch/finally  
 Niezawodność `try/catch/finally` to mechanizm, za pomocą takiego samego poziomu gwarancji przewidywalności jako niezarządzana wersja obsługi wyjątków. `catch/finally` Blok jest CER. W bloku metody wymagają przygotowań i musi być noninterruptible.  
  
 W programie .NET Framework 2.0, kod informuje środowisko uruchomieniowe try to niezawodne, wywołując <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezpośrednio przed blokiem try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> jest elementem członkowskim <xref:System.Runtime.CompilerServices.RuntimeHelpers>, klasę obsługi kompilatora. Wywołaj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezpośrednio do czasu jej udostępnienia ich za pomocą kompilatorów.  
  
## <a name="noninterruptible-regions"></a>Regiony Noninterruptible  
 Noninterruptible region grupuje zestaw instrukcji do CER.  
  
 W programie .NET Framework w wersji 2.0, do czasu udostępnienia ich za pomocą obsługa kompilatora kod użytkownika, tworzy bez przerywania regionów przy użyciu niezawodnych try/catch/finally, zawiera blok try/catch pusty poprzedzone <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> wywołania metody.  
  
## <a name="critical-finalizer-object"></a>Obiekt krytyczny Finalizator  
 A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> gwarantuje, że wyrzucanie elementów bezużytecznych będzie wykonywał finalizatora. Po alokacji finalizator i jego wykresu wywołań są przygotowany wcześniej. Metodzie finalizacji wykonuje CER, a następnie należy przestrzegać wszystkich ograniczeń CERs i finalizatorów.  
  
 Żadnych typów dziedziczących <xref:System.Runtime.InteropServices.SafeHandle> i <xref:System.Runtime.InteropServices.CriticalHandle> jest gwarantowane ma finalizator, ich wykonania w ramach CER. Implementowanie <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> w <xref:System.Runtime.InteropServices.SafeHandle> pochodne klasy do wykonywania kodu, który jest wymagany, aby zwolnić uchwytu.  
  
## <a name="code-not-permitted-in-cers"></a>Kod nie jest dozwolona w CERs  
 Następujące operacje nie są dozwolone w CERs:  
  
- Jawne alokacji.  
  
- Pobieranie blokady.  
  
- Pakowanie.  
  
- Dostęp do tablicy wielowymiarowej.  
  
- Metoda wywołania przy użyciu odbicia.  
  
- <xref:System.Threading.Monitor.Enter%2A> lub <xref:System.IO.FileStream.Lock%2A>.  
  
- Sprawdzanie zabezpieczeń. Wykonaj żądania, nie tylko Konsolidacja zapotrzebowania.  
  
- <xref:System.Reflection.Emit.OpCodes.Isinst> i <xref:System.Reflection.Emit.OpCodes.Castclass> dla obiektów COM i serwery proxy  
  
- Pobieranie lub ustawianie pól w przezroczystym serwerem proxy.  
  
- Serializacji.  
  
- Wskaźniki funkcji i obiektów delegowanych.  
  
## <a name="see-also"></a>Zobacz także

- [Najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md)
