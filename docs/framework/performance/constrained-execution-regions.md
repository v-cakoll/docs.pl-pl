---
title: Ograniczone regiony wykonania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 81de172df01879af97aa66b0892a97505178c93c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="constrained-execution-regions"></a>Ograniczone regiony wykonania
Region ograniczonego wykonania (CER) jest częścią mechanizm tworzenia niezawodnego kodu zarządzanego. CER definiuje obszar, w którym środowisko uruchomieniowe języka wspólnego (CLR) jest ograniczony z zgłaszanie wyjątków poza pasmem, które uniemożliwiłyby kodu w obszarze wykonywanie w całości. W tym regionie kod użytkownika jest ograniczane wykonywanie kodu, który spowoduje zgłaszanie wyjątków poza pasmem. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Metody musi bezpośrednio poprzedzać `try` bloku i znaczniki `catch`, `finally`, i `fault` bloki jako ograniczone regiony wykonania. Gdy oznaczony jako region ograniczonego, kod musi wywoływać tylko innych kodu za pomocą kontrakty niezawodności silne i kodu nie może przydzielić lub należy wirtualnego wywołania metod nieprzygotowany lub zawodnych, chyba że kod jest przygotowany do obsługi błędów. Przerywa wątku opóźnienia CLR dla kodu, który jest wykonywany w CER.  
  
 Ograniczone regiony wykonania są używane w różnych formularzach CLR oprócz adnotacjami `try` zablokować, szczególnie krytyczne finalizatory wykonywanie w klasach pochodzących od <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> klasy i wykonywane przy użyciu kodu <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody.  
  
## <a name="cer-advance-preparation"></a>Przygotowań CER  
 Środowisko CLR przygotowuje CERs z wyprzedzeniem, aby uniknąć warunków braku pamięci. Przygotowań jest wymagana, więc CLR nie powoduje, że stan braku pamięci podczas ładowania w czasie kompilacji lub typu.  
  
 Deweloper jest wymagany do wskazywania CER kod regionu:  
  
-   Najwyższego poziomu region CER i metod w wykresu wywołań pełne, które mają <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> atrybutu stosowane są przygotowywane z wyprzedzeniem. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Można tylko stan gwarancji <xref:System.Runtime.ConstrainedExecution.Cer.Success> lub <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
-   Nie można wykonać przygotowań do wywołania, które statycznie nieokreślonym, takie jak wirtualne wysyłania. Użyj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody w tych przypadkach. Korzystając z <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> metody <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> atrybut powinien zostać zastosowany do kodu oczyszczania.  
  
## <a name="constraints"></a>Ograniczenia  
 Użytkownicy są ograniczone w typ kodu, które mogą zapisywać w CER. Kod nie może spowodować wyjątek poza pasmem, takich jak mogą wynikać z następujących czynności:  
  
-   Jawny przydział.  
  
-   OPAKOWYWANIE.  
  
-   Uzyskiwanie blokady.  
  
-   Wywołanie metod nieprzygotowany praktycznie.  
  
-   Wywoływanie metody z kontraktem słabych lub nieistniejącą niezawodności.  
  
 W programie .NET Framework w wersji 2.0 tych warunków ograniczających oznaczają wskazówki. Diagnostyka są realizowane za pośrednictwem narzędzi analizy kodu.  
  
## <a name="reliability-contracts"></a>Kontrakty niezawodności  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Jest niestandardowy atrybut, który dokumentów gwarancje niezawodności i stanu uszkodzenia danej metody.  
  
### <a name="reliability-guarantees"></a>Gwarancje niezawodności  
 Gwarancje niezawodności, reprezentowany przez <xref:System.Runtime.ConstrainedExecution.Cer> wartości wyliczenia określają stopień niezawodności danej metody:  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. W wyjątkowych okolicznościach metoda może zakończyć się niepowodzeniem. W tym przypadku metoda raportuje ją do wywoływania metody zakończyło się pomyślnie, lub nie powiodło się. Metoda musi być zawarty w CER, aby upewnić się, czy może raportować wartość zwracaną.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.None>. Metoda, typu lub zestawu ma nie zawierają CER i prawdopodobnie nie bezpiecznie wywołać w CER bez znaczne ograniczenie stanu uszkodzenia. Nie przyjmuje zaletą gwarancje CER. Oznacza to następujące czynności:  
  
    1.  W warunkach wyjątkowych metody może zakończyć się niepowodzeniem.  
  
    2.  Metoda może być lub może nie raportować, że nie.  
  
    3.  Metoda nie są zapisywane do użycia CER, najbardziej prawdopodobnym scenariuszem.  
  
    4.  Jeśli metoda, typu lub zestawu nie jest jawnie zidentyfikowana została wykonana pomyślnie, jest niejawnie identyfikowane jako <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.Success>. W wyjątkowych okolicznościach metody jest gwarantowana powiodło się. Aby osiągnąć ten poziom niezawodności należy zawsze konstruować CER wokół metodę, która jest wywoływana, nawet gdy jest wywoływana z regionu z systemem innym niż CER. Metoda zakończy się pomyślnie, jeśli rozwiązanie przeznaczenie, mimo że można wyświetlić subiektywnie Powodzenie. Na przykład oznaczenia liczbę za pomocą `ReliabilityContractAttribute(Cer.Success)` oznacza, że po uruchomieniu w CER zawsze zwraca liczbę liczba elementów w <xref:System.Collections.ArrayList> i nigdy nie może narazić pola wewnętrzne w stanie nieokreślony.  Jednak <xref:System.Threading.Interlocked.CompareExchange%2A> — metoda jest oznaczona jako Powodzenie również, pamiętając, że powodzenie może oznaczać wartość mogły nie zostać zastąpione z nową wartością z powodu sytuacji wyścigu.  Punkt klucza jest metoda działa w taki sposób, który jest udokumentowany zachowuje się, czy kod CER nie zachodzi potrzeba zapisania oczekiwać żadnych nietypowe zachowanie poza jakie poprawna, ale zawodnych kod powinien wyglądać tak.  
  
### <a name="corruption-levels"></a>Uszkodzenie poziomów  
 Poziomy uszkodzenie reprezentowany przez <xref:System.Runtime.ConstrainedExecution.Consistency> wartości wyliczenia, wskazuje, ile stanu może być uszkodzona w danym środowisku:  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. W wyjątkowych okolicznościach środowisko uruchomieniowe języka wspólnego (CLR) zapewnia nie gwarancji dotyczących stanu spójności w bieżącej domenie aplikacji.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. W wyjątkowych okolicznościach metody jest gwarantowane ograniczyć uszkodzenia stanu do bieżącego wystąpienia.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, W wyjątkowych okolicznościach CLR sprawia, że nie gwarancji dotyczących stanu spójności; oznacza to, że ten stan może spowodować jej uszkodzenie procesu.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. W wyjątkowych okolicznościach metody jest gwarantowane nie doprowadzić do uszkodzenia.  
  
## <a name="reliability-trycatchfinally"></a>Niezawodność try/catch/finally  
 Niezawodność `try/catch/finally` jest obsługa mechanizmu o tym samym poziomie gwarancje przewidywalności jako niezarządzanej wersji wyjątków. `catch/finally` Blok jest CER. W bloku metody wymagają przygotowań i musi być noninterruptible.  
  
 W programie .NET Framework w wersji 2.0, kod informuje środowiska uruchomieniowego try jest niezawodne przez wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezpośrednio przed blokiem try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>jest elementem członkowskim <xref:System.Runtime.CompilerServices.RuntimeHelpers>, klasa pomocy technicznej kompilatora. Wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bezpośrednio do czasu jego dostępność za pośrednictwem kompilatory.  
  
## <a name="noninterruptible-regions"></a>Regiony Noninterruptible  
 Noninterruptible region grupuje zestaw instrukcji w CER.  
  
 W .NET Framework w wersji 2.0, do czasu pojawienia się za pośrednictwem obsługa kompilatora, kod użytkownika tworzy bez przerywania regionów z niezawodnej try/catch/finally, który zawiera blok try/catch pusty poprzedzone <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> wywołania metody.  
  
## <a name="critical-finalizer-object"></a>Krytyczne finalizatora obiektu  
 A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> gwarantuje, że wyrzucanie elementów bezużytecznych wykona finalizatora. Po alokacji, finalizator i jego wykresu wywołań przygotować z wyprzedzeniem. Metoda finalizator wykonuje w CER, a musi przestrzegać wszystkich ograniczeń na CERs i finalizatory.  
  
 Żadnych typów dziedziczących po <xref:System.Runtime.InteropServices.SafeHandle> i <xref:System.Runtime.InteropServices.CriticalHandle> dotrą do ma finalizator, ich wykonania w CER. Implementowanie <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> w <xref:System.Runtime.InteropServices.SafeHandle> klas do wykonania kodu, który jest wymagany, aby zwolnić dojścia pochodnych.  
  
## <a name="code-not-permitted-in-cers"></a>Kod nie jest dozwolona w CERs  
 Następujące operacje są niedozwolone w CERs:  
  
-   Jawne alokacji.  
  
-   Uzyskiwanie blokady.  
  
-   OPAKOWYWANIE.  
  
-   Dostęp do tablicy wielowymiarowej.  
  
-   Metoda wywołania przy użyciu odbicia.  
  
-   <xref:System.Threading.Monitor.Enter%2A>lub <xref:System.IO.FileStream.Lock%2A>.  
  
-   Sprawdzanie zabezpieczeń. Wykonaj żądania, nie tylko Połącz wymagań.  
  
-   <xref:System.Reflection.Emit.OpCodes.Isinst>i <xref:System.Reflection.Emit.OpCodes.Castclass> dla obiektów COM i serwerów proxy  
  
-   Pobierania lub ustawiania pól na przezroczystego obiektu pośredniczącego.  
  
-   Serializacji.  
  
-   Wskaźniki funkcji i obiektów delegowanych.  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md)
