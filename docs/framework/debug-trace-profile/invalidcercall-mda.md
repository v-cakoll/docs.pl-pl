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
ms.openlocfilehash: 1a68aac2a92a0569e288da858e4a4e4695fd5eaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754431"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy jest połączenie w ramach ograniczonego wykonania wykres region (CER) do metody, która ma umowy niezawodność lub kontrakt zbyt słabe. Słabe kontrakt jest kontraktu, który oświadcza, że najgorszy uszkodzenie stan przypadku zakresu większą niż wystąpienie podawaną do wywołania, czyli <xref:System.AppDomain> lub stan procesu może ulec uszkodzeniu lub jego wynik nie jest zawsze obliczana w sposób deterministyczny gdy jest wywoływany w CER.  
  
## <a name="symptoms"></a>Symptomy  
 Nieoczekiwane wyniki podczas wykonywania kodu w CER. Objawy nie są określone. Może być nieoczekiwany <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, lub inne wyjątki w wywołaniu do metody zawodnych ponieważ środowisko wykonawcze nie wcześniejsze przygotowanie ani go chronić <xref:System.Threading.ThreadAbortException> wyjątków w czasie wykonywania. Większe zagrożenie jest, że każdy wyjątek, wynikające z metody w czasie wykonywania można pozostawić <xref:System.AppDomain> lub procesów w niestabilnym stanie, który jest sprzeczne z celem CER. Powodów, dla którego utworzono CER jest aby uniknąć uszkodzenia stan takich. Objawy uszkodzonego jest określone dla aplikacji, ponieważ definicja spójne różni się między aplikacjami.  
  
## <a name="cause"></a>Przyczyna  
 Kod w CER jest wywołanie funkcji bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> lub za pomocą ograniczymy <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> nie jest zgodny z systemem w CER.  
  
 W odniesieniu do składni kontraktu niezawodności, słabe kontraktu jest kontraktu, który nie określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość wyliczenia lub Określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, lub <xref:System.Runtime.ConstrainedExecution.Cer.None>. Którykolwiek z tych warunków wskazuje, że kod wywołuje może utrudniać wysiłek inny kod w CER do utrzymania spójnego stanu.  CERs Zezwalaj na kod, aby traktować błędy w sposób deterministyczny bardzo, utrzymywanie invariants wewnętrznych, które są istotne dla aplikacji i zezwalając na kontynuowanie działania w twarz błędów przejściowych, takich jak wyjątki o braku pamięci.  
  
 Aktywacja to zdarzenie MDA oznacza możliwość wywołania metody w CER może zakończyć się niepowodzeniem w taki sposób, że obiekt wywołujący nie oczekiwano elementu lub które pozostawia <xref:System.AppDomain> lub przetwarzać stan uszkodzony lub ulegnie nieodwracalnej awarii. Oczywiście dzwonić kodu może być wykonywany poprawnie, a problem jest po prostu nieistniejącego kontraktu. Jednak zagadnień związanych z pisanie niezawodnego kodu jest delikatny i brak kontrakt jest dobry wskaźnik, który kod może nie zostać prawidłowo wykonany. Kontrakty te z nich są wskaźnikami, które programistę ma kodowane w niezawodny sposób będą również zapewnia, że te gwarancje nie zmieni się w przyszłości poprawki kodu.  Oznacza to kontrakty te są deklaracje intencji i nie tylko szczegółów implementacji.  
  
 Ponieważ dowolną metodą mającą słabych lub nieistniejącego kontraktu mogą ulec awarii w wiele właściwie nieprzewidywalnych sposobów, środowisko wykonawcze nie próbuje usunąć żadnego z własną nieprzewidziane błędy w metodę, która wynikające z opóźnieniem JIT — kompilowanie, słownik typów ogólnych wypełnianie, Wątek przerywa, na przykład. Oznacza to gdy to zdarzenie MDA jest aktywowane, oznacza to, czy środowisko wykonawcze nie zostały dołączone metodę wywołania CER definiowanego; wykresu wywołań został zakończony w tym węźle, ponieważ przygotować to poddrzewo w dalszym ciągu pomógłby maski potencjalnych błędów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Dodaj umowy prawidłowe niezawodności do funkcji lub wywołanie tej funkcji należy unikać.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Efekt wywoływanie słabe umowy z CER może być awaria CER do ukończenia jej operacje. Może to prowadzić do uszkodzenia <xref:System.AppDomain> przetwarzania stanu.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowe dane wyjściowe z tego MDA.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
