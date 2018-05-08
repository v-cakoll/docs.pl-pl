---
title: invalidCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15f41ebd961f25979fe569fd89dd2135a0a6cd41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall` Zarządzany Asystent debugowania (MDA) została aktywowana po wywołaniu wykresu (CER) region ograniczonego wykonania metody, która ma nie kontraktu niezawodności lub zbyt słabe kontraktu. Kontrakt słabe jest kontraktu, który deklaruje, że najgorszy uszkodzenie wielkość stanu jest zakresu większy niż wystąpienie przekazany do wywołania, oznacza to, <xref:System.AppDomain> lub stan procesu może ulec uszkodzeniu lub jego wynik nie jest zawsze sposób niejednoznaczny Obliczanie gdy jest wywoływany w CER.  
  
## <a name="symptoms"></a>Symptomy  
 Nieoczekiwane wyniki podczas wykonywania kodu w CER. Objawy nie są określone. Może być nieoczekiwane <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, lub inne wyjątków w wywołaniu metody zawodnych ponieważ środowisko uruchomieniowe nie wcześniejsze przygotowanie ani go chronić <xref:System.Threading.ThreadAbortException> wyjątków w czasie wykonywania. Większe zagrożenie jest, że wszystkie wyjątki wynikające z metody w czasie wykonywania można pozostawić <xref:System.AppDomain> lub procesów w niestabilnym stanie, czyli sprzeczności z celem CER. Utworzone CER dzieje się tak aby uniknąć uszkodzenia stanu, takich jak ta. Objawy uszkodzonego są określone dla aplikacji definicji spójna różni się między aplikacjami.  
  
## <a name="cause"></a>Przyczyna  
 Kod w CER powoduje wywołanie funkcji bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> lub niska <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> który nie jest zgodny z systemem w CER.  
  
 W odniesieniu do składni kontraktu niezawodności, kontrakt słabe jest kontraktu, która nie określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość wyliczenia lub Określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, lub <xref:System.Runtime.ConstrainedExecution.Cer.None>. Jeden z następujących warunków wskazuje, że kod wywołuje może utrudnić próby Obsługa spójna innego kodu w CER.  CERs umożliwić kodu traktować błędy w sposób bardzo deterministyczna, obsługa invariants wewnętrznego, które są ważne dla aplikacji, dzięki czemu jego dalsze działanie jest w fazie przejściowej błędów, takich jak wyjątki o braku pamięci.  
  
 Aktywacja to zdarzenie MDA wskazuje możliwość metoda wywoływana w CER może zakończyć się niepowodzeniem w sposób zapewniający element wywołujący nie oczekiwano lub który pozostawia <xref:System.AppDomain> lub przetworzyć stan uszkodzony lub ich nieodwracalnej utraty. Oczywiście wywoływanego kodu może zostać prawidłowo wykonany, a problem jest po prostu nieistniejącego kontraktu. Jednak zagadnień związanych z pisanie niezawodnego kodu są niewielkie i brak kontrakt jest dobry wskaźnik, którego kod może nie zostać prawidłowo wykonany. Kontrakty te z nich są wskaźnikami programistę zawiera kodowany niezawodnie, a także gwarantuje, że te gwarancje nie zmieni się w przyszłości poprawki kodu.  Oznacza to, że kontrakty te są deklaracje zamierzone i nie tylko szczegóły implementacji.  
  
 Ponieważ dowolnej metody z kontraktem słabych lub nieistniejącą mogą ulec awarii w wielu nieprzewidywalnych sposobów, środowisko uruchomieniowe nie jest podejmowana próba Usuń wszystkie własną nieprzewidywalne błędów z metody, które zostały wprowadzone przez opóźnieniem JIT — kompilowanie, słownika ogólne wypełnianie lub wątku jest przerywana, np. Oznacza to po aktywowaniu to zdarzenie MDA wskazuje on, że środowisko wykonawcze nie zawiera wywołaną metodę w CER definiowanego; wykresu wywołań zostało zakończone w tym węźle, ponieważ kontynuowanie przygotowanie to poddrzewo byłaby pomocna zamaskować potencjalnych błędów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Dodaj kontrakt niezawodności prawidłowy funkcji lub Unikaj używania tego wywołania funkcji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Efekt wywoływanie słabe umowy z CER może być błąd CER do wykonania operacji. Może to spowodować uszkodzenie <xref:System.AppDomain> przetworzyć stanu.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowe dane wyjściowe to zdarzenie MDA.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
