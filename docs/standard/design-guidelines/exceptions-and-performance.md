---
title: Wyjątki i wydajność
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: e3a7fa0f284ebf028a18cae37c050d7ceda9bb79
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709390"
---
# <a name="exceptions-and-performance"></a>Wyjątki i wydajność
Jeden typowy problem związany z wyjątkami polega na tym, że jeśli wyjątki są używane dla kodu, który rutynowie kończy się niepowodzeniem, wydajność implementacji będzie nieakceptowalna. Jest to prawidłowy problem. Gdy element członkowski zgłasza wyjątek, jego wydajność może być Rzędna wolniej. Istnieje jednak możliwość osiągnięcia odpowiedniej wydajności, ale ściśle przestrzeganie wytycznych dotyczących wyjątków, które nie zezwalają na używanie kodów błędów. Dwa wzorce opisane w tej sekcji sugerują sposoby wykonania tej czynności.

 **X DO NOT** używa kody błędów ze względu na problemy, czy wyjątki może negatywnie wpłynąć na wydajność.

 Aby zwiększyć wydajność, można użyć wzorca testera-DOER lub wzorca try-Parse, opisanego w następnych dwóch sekcjach.

## <a name="tester-doer-pattern"></a>Tester — wzorzec DOER
 Czasami można poprawić wydajność zgłaszanego przez wyjątek, dzieląc element członkowski na dwa. Przyjrzyjmy się metodzie <xref:System.Collections.Generic.ICollection%601.Add%2A> interfejsu <xref:System.Collections.Generic.ICollection%601>.

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 Metoda `Add` zgłasza, czy kolekcja jest tylko do odczytu. Może to być problem z wydajnością w scenariuszach, w których wywoływanie metody często kończy się niepowodzeniem. Jednym ze sposobów, aby wyeliminować problem, jest przetestowanie, czy kolekcja jest zapisywalna przed podjęciem próby dodania wartości.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 Element członkowski używany do testowania warunku, który w naszym przykładzie jest właściwością `IsReadOnly`, jest określany jako tester. Element członkowski używany do wykonywania potencjalnie wyrzucania operacji, Metoda `Add` w naszym przykładzie jest określana jako DOER.

 **✓ CONSIDER** wzorzec Tester Doer dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.

## <a name="try-parse-pattern"></a>Wzorzec try-Parse
 W przypadku skrajnie wrażliwych na wydajność interfejsów API, jeszcze szybszym wzorcem niż wzorzec test-DOER opisany w poprzedniej sekcji. Wzorzec wywołuje zmianę nazwy elementu członkowskiego, aby uczynić dobrze zdefiniowanym przypadkiem testowym częścią semantyki elementu członkowskiego. Na przykład <xref:System.DateTime> definiuje metodę <xref:System.DateTime.Parse%2A>, która zgłasza wyjątek, jeśli analizowanie ciągu kończy się niepowodzeniem. Definiuje również odpowiednią metodę <xref:System.DateTime.TryParse%2A>, która próbuje przeanalizować, ale zwraca wartość false, jeśli analiza nie powiedzie się i zwróci wynik pomyślnej analizy przy użyciu parametru `out`.

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 W przypadku korzystania z tego wzorca ważne jest, aby zdefiniować funkcje try w rygorystycznych warunkach. Jeśli element członkowski nie powiedzie się z jakiegokolwiek powodu, który jest inny niż wyraźnie zdefiniowane, element członkowski musi nadal zgłosić odpowiedni wyjątek.

 **✓ CONSIDER** wzorzec spróbuj analizy dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.

 **✓ DO** Użyj prefiksu "Try" i wartość logiczną zwracanego typu dla metody implementacja tego wzorca.

 **✓ DO** Podaj elementu członkowskiego zgłaszanie wyjątków dla każdego elementu członkowskiego przy użyciu wzorca spróbuj analizy.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)
