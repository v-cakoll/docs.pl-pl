---
title: Wyjątki i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d664b7b61394bd9bfe6d0abd7130f9f0191e7a03
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083549"
---
# <a name="exceptions-and-performance"></a>Wyjątki i wydajność
Jednym problemem wspólnej związanym z wyjątków jest, że wyjątki są używane do kodu, który regularnie zakończy się niepowodzeniem, wydajność wdrożenia zostaną niedopuszczalne. Jest to prawidłowy niepożądane. Gdy członek zgłasza wyjątek, jego wydajność może być rzędów wolniej. Jednak jest możliwe uzyskanie wysoką wydajność podczas ściśle przestrzega wytycznych wyjątków, które nie zezwalają na używanie kodów błędów. Dwa wzorce opisane w tej sekcji sugerują sposoby wykonania tej czynności.  
  
 **X DO NOT** używa kody błędów ze względu na problemy, czy wyjątki może negatywnie wpłynąć na wydajność.  
  
 Aby zwiększyć wydajność, jest możliwe użycie wzorca Tester Doer lub wzorzec spróbuj analizy, opisane w dwóch następnych sekcjach.  
  
## <a name="tester-doer-pattern"></a>Wzorzec Tester Doer  
 Czasami można poprawić wydajność, elementu członkowskiego Zgłaszanie wyjątku w, dzieląc element członkowski do dwóch. Przyjrzyjmy się <xref:System.Collections.Generic.ICollection%601.Add%2A> metody <xref:System.Collections.Generic.ICollection%601> interfejsu.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 Metoda `Add` zgłasza wyjątek, jeśli kolekcja jest tylko do odczytu. Może to być problem z wydajnością w scenariuszach, gdzie oczekiwano wywołania metody które często nie powiedzie się. Sposoby, aby rozwiązać ten problem jest do sprawdzenia, czy kolekcja jest zapisywalny, zanim spróbujesz dodać wartość.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Element członkowski, używany do sprawdzania warunku, który w tym przykładzie jest to właściwość `IsReadOnly`, jest określany jako tester. Element członkowski, używany do wykonywania operacji potencjalnie zgłaszanie, `Add` metody w naszym przykładzie jest określany jako doer.  
  
 **✓ CONSIDER** wzorzec Tester Doer dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.  
  
## <a name="try-parse-pattern"></a>Try-Parse wzorzec  
 W przypadku interfejsów API bardzo wrażliwego na wydajność należy użyć wzorca jeszcze szybciej niż wzorzec Tester Doer opisanego w poprzedniej sekcji. Wzorzec wymaga dostosowania nazwy elementu członkowskiego się dobrze zdefiniowanych testu zamierzone, Zapisz część semantyki elementu członkowskiego. Na przykład <xref:System.DateTime> definiuje <xref:System.DateTime.Parse%2A> metodę, która zgłasza wyjątek, jeśli podczas analizowania ciągu kończy się niepowodzeniem. Definiuje również odpowiedni <xref:System.DateTime.TryParse%2A> metodę, która próbuje zanalizować, ale zwraca wartość false w przypadku analizowania zakończy się niepowodzeniem i zwraca wynik pomyślnie analizy przy użyciu `out` parametru.  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 Korzystając z tego wzorca, należy zdefiniować funkcje spróbuj w warunkach strict. Jeśli element członkowski nie powiedzie się z innego powodu niż spróbuj dobrze zdefiniowanych, elementu członkowskiego musi nadal wyjątku odpowiednie.  
  
 **✓ CONSIDER** wzorzec spróbuj analizy dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.  
  
 **✓ DO** Użyj prefiksu "Try" i wartość logiczną zwracanego typu dla metody implementacja tego wzorca.  
  
 **✓ DO** Podaj elementu członkowskiego zgłaszanie wyjątków dla każdego elementu członkowskiego przy użyciu wzorca spróbuj analizy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)
