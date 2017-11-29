---
title: "Wyjątki i wydajności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c2d7cfcb228c492d2adbe614d0ed88a3b02bb68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exceptions-and-performance"></a>Wyjątki i wydajności
Jednej wspólnej problemem związanym z wyjątkami jest, że wyjątki są używane do kodu, który regularnie zakończy się niepowodzeniem, wydajność implementacji zostaną nie do przyjęcia. Jest to prawidłowy niepożądane. Gdy członek zgłasza wyjątek, jego wydajność może być rzędów wolniej. Jednak jest możliwe uzyskanie dobrą wydajność ściśle przestrzegając wskazówki wyjątków, które nie zezwalaj na korzystanie z kodów błędów. Dwa wzorce opisane w tej sekcji sugestie sposobów, w tym celu.  
  
 **X nie** używa kody błędów ze względu na problemy, czy wyjątki może negatywnie wpłynąć na wydajność.  
  
 Aby zwiększyć wydajność, jest możliwość użycia wzorca Tester Doer lub wzorcu analizy spróbuj opisanego w dwóch następnych sekcjach.  
  
## <a name="tester-doer-pattern"></a>Wzorzec Tester Doer  
 Czasami można poprawić wydajność elementu członkowskiego Zgłaszanie wyjątku przez dzielenie element członkowski na dwie części. Przyjrzyjmy się <xref:System.Collections.Generic.ICollection%601.Add%2A> metody <xref:System.Collections.Generic.ICollection%601> interfejsu.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 Metoda `Add` zgłasza wyjątek, jeśli kolekcja jest tylko do odczytu. Może to być problem z wydajnością w scenariuszach, w których można oczekiwać wywołanie metody często niepowodzenie. Jednym ze sposobów złagodzić problem jest aby sprawdzić, czy kolekcja jest zapisywalny, przed podjęciem próby dodania wartości.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Element członkowski wykorzystywane do testowania warunek, który w naszym przykładzie jest właściwość `IsReadOnly`, jest określany jako tester. Element członkowski używany do wykonywania operacji potencjalnie przerzucane, `Add` metody w tym przykładzie jest określana jako doer.  
  
 **ROZWAŻ ✓** wzorzec Tester Doer dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.  
  
## <a name="try-parse-pattern"></a>Spróbuj analizy wzorca  
 W przypadku bardzo ważnych wydajności interfejsów API należy użyć wzorzec szybszy niż wzorzec Tester Doer opisanych w poprzedniej sekcji. Wzorzec wywołuje dostosowywania nazwę elementu członkowskiego, aby dobrze zdefiniowany testu przypadek część semantyki elementu członkowskiego. Na przykład <xref:System.DateTime> definiuje <xref:System.DateTime.Parse%2A> metodę, która zgłasza wyjątek, jeśli podczas analizowania ciągu nie powiedzie się. Definiuje również odpowiedniego <xref:System.DateTime.TryParse%2A> metodę, która podejmuje próbę analizy, ale zwraca wartość false, jeśli podczas analizowania zakończy się niepowodzeniem i zwraca wynik w pomyślnym analizy przy użyciu `out` parametru.  
  
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
  
 Podczas używania tego wzorca, jest zdefiniowanie funkcji spróbuj względem strict. W przypadku niepowodzenia element członkowski przyczyn innych niż spróbuj dobrze zdefiniowany element członkowski musi nadal throw odpowiednich wyjątków.  
  
 **ROZWAŻ ✓** wzorzec spróbuj analizy dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.  
  
 **CZY ✓** Użyj prefiksu "Try" i wartość logiczną zwracanego typu dla metody implementacja tego wzorca.  
  
 **CZY ✓** Podaj elementu członkowskiego zgłaszanie wyjątków dla każdego elementu członkowskiego przy użyciu wzorca spróbuj analizy.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówek dotyczących wyjątków](../../../docs/standard/design-guidelines/exceptions.md)
