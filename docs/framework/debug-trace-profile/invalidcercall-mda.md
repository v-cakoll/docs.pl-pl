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
ms.openlocfilehash: f8e467401f7c50898613c7cf6eca68a8a705431a
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217392"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
Asystent debugowania zarządzanego `invalidCERCall` (MDA) jest uaktywniany w przypadku wywołania w grafie ograniczonego regionu wykonywania (CER) do metody, która nie ma umowy dotyczącej niezawodności lub nadmiernie słabego kontraktu. Słaby kontrakt jest umową, która deklaruje, że najgorszy stan awarii jest większy niż wystąpienie przesłane do wywołania, to oznacza, że <xref:System.AppDomain> lub stan procesu może ulec uszkodzeniu lub jego wynik nie zawsze jest deterministyczny obliczanej po wywołaniu w CER.  
  
## <a name="symptoms"></a>Objawy  
 Nieoczekiwane wyniki podczas wykonywania kodu w CER. Objawy nie są określone. Mogą to być nieoczekiwane <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>lub inne wyjątki w wywołaniu metody zawodnej, ponieważ środowisko uruchomieniowe nie przygotowało go wcześniej ani nie chroni przed <xref:System.Threading.ThreadAbortException> wyjątkami w czasie wykonywania. Większe zagrożenie polega na tym, że każdy wyjątek wynikający z metody w czasie wykonywania może opuścić <xref:System.AppDomain> lub proces w stanie niestabilnym, który jest sprzeczny z celem CER. Przyczyną jest to, że jest tworzone CER, aby uniknąć uszkodzenia stanu. Objawy uszkodzenia stanu są specyficzne dla aplikacji, ponieważ definicja spójnego stanu różni się między aplikacjami.  
  
## <a name="cause"></a>Przyczyna  
 Kod w programie CER wywołuje funkcję bez <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> lub z słabym <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>, która nie jest zgodna z działaniem w CER.  
  
 W odniesieniu do składni kontraktu niezawodności słaby kontrakt jest kontraktem, który nie określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartości wyliczenia lub określa <xref:System.Runtime.ConstrainedExecution.Consistency> wartość <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>lub <xref:System.Runtime.ConstrainedExecution.Cer.None>. Każdy z tych warunków wskazuje, że wywoływany kod może utrudniać wysiłki innego kodu w CER, aby zachować spójny stan.  CERs dopuszczaj kod, aby traktować błędy w bardzo deterministyczny sposób, utrzymując wewnętrzne nieposiadające znaczące znaczenie dla aplikacji i umożliwiając jej kontynuowanie działania w przypadku błędów przejściowych, takich jak wyjątki braku pamięci.  
  
 Aktywacja tego elementu MDA wskazuje na to, że metoda wywoływana w CER może zakończyć się niepowodzeniem w taki sposób, że obiekt wywołujący nie oczekiwał lub opuszcza <xref:System.AppDomain> lub stan procesu uszkodzony lub nieodwracalny. Oczywiście wywoływany kod może działać poprawnie, a problem jest po prostu nieobecnym kontraktem. Jednak problemy związane z pisaniem niezawodnego kodu są delikatne i brak kontraktu jest dobrym wskaźnikiem, że kod może nie działać poprawnie. Umowy są wskaźnikami, że programista zakodowano niezawodnie, a także niesie obietnice zwiększenia, że te gwarancje nie zmienią się w przyszłości.  Oznacza to, że umowy są deklaracjami intencji, a nie tylko szczegółami implementacji.  
  
 Ponieważ jakakolwiek metoda z nieoczekiwanym lub nieistniejącym kontraktem może zakończyć się niepowodzeniem na wiele nieprzewidywalnych sposobów, środowisko uruchomieniowe nie podejmuje próby usunięcia jakichkolwiek nieprzewidywalnych błędów z metody, które są wprowadzane przez kompilację JIT z opóźnieniem. na przykład populacja lub przerwania wątku. Oznacza to, że po aktywowaniu tego MDA wskazuje, że środowisko uruchomieniowe nie uwzględnia wywołanej metody w zdefiniowanym elemencie CER. Wykres wywołań został przerwany w tym węźle, ponieważ kontynuowanie przygotowania tego poddrzewa ułatwi zamaskowanie potencjalnego błędu.  
  
## <a name="resolution"></a>Rozwiązanie  
 Dodaj prawidłowy kontrakt niezawodności do funkcji lub Unikaj korzystania z tego wywołania funkcji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Efekt wywołania słabego kontraktu z CER może być błędem CER, aby zakończyć jego operacje. Może to prowadzić do uszkodzenia stanu procesu <xref:System.AppDomain>.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
