---
title: Odrzuty — przewodnik po języku C#
description: Opisuje obsługę języka C#dla odrzutów, które są nieprzypisane, zmienne odrzutowe i sposoby, w jakie można używać odrzutów.
ms.technology: csharp-fundamentals
ms.date: 07/21/2017
ms.openlocfilehash: a76e7fc13f92ec0de87153bb35eb3924bb317616
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100637"
---
# <a name="discards---c-guide"></a>Odrzuty — przewodnik po języku C#

Począwszy od języka C# 7.0, C# obsługuje odrzuty, które są tymczasowe, fikcyjne zmienne, które są celowo nieużywane w kodzie aplikacji. Odrzuty są równoważne zmiennym nieprzypisanych; nie mają wartości. Ponieważ istnieje tylko jedna zmienna odrzutu, a ta zmienna może nawet nie być przydzielona do magazynu, odrzuty mogą zmniejszyć alokacje pamięci. Ponieważ sprawiają, że intencja kodu jest jasna, zwiększają jego czytelność i łatwość konserwacji.

Wskazujesz, że zmienna jest odrzuceniem,`_`przypisując jej znak podkreślenia ( ) jako swoją nazwę. Na przykład następujące wywołanie metody zwraca 3-krotkę, w której pierwszą i drugą wartością są odrzuty, a *obszar* jest wcześniej zadeklarowaną zmienną, która ma być ustawiona na odpowiedni trzeci składnik zwrócony przez *GetCityInformation:*

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

W języku C# 7.0 odrzuty są obsługiwane w przydziałach w następujących kontekstach:

- [Dekonstrukcja](deconstruct.md)krotki i obiektu .
- Dopasowanie wzorca z [jest](language-reference/keywords/is.md) i [przełącznik](language-reference/keywords/switch.md).
- Wywołania metod `out` z parametrami.
- `_` Autonomiczny, gdy `_` nie jest w zakresie.

Gdy `_` jest prawidłowym odrzuceniem, próba pobrania jego wartości lub użycia jej w operacji przypisania generuje\_błąd kompilatora CS0301, "Nazwa ' ' nie istnieje w bieżącym kontekście". Dzieje się `_` tak, ponieważ nie jest przypisana wartość i nie można nawet przypisać lokalizacji magazynu. Jeśli była to zmienna rzeczywista, nie można odrzucić więcej niż jednej wartości, tak jak w poprzednim przykładzie.

## <a name="tuple-and-object-deconstruction"></a>Dekonstrukcja krotki i obiektu

Odrzuty są szczególnie przydatne w pracy z krotek, gdy kod aplikacji używa niektórych elementów krotki, ale ignoruje inne. Na przykład następująca `QueryCityDataForYears` metoda zwraca 6-krotka z nazwą miasta, jego obszar, rok, ludności miasta w tym roku, drugi rok, a ludności miasta w tym drugim roku. Przykład pokazuje zmianę populacji między tymi dwoma latami. Z danych dostępnych z krotki, nie jesteśmy zainteresowani obszarem miasta, znamy nazwę miasta i dwie daty w czasie projektowania. W rezultacie jesteśmy zainteresowani tylko dwie wartości populacji przechowywane w krotce i może obsługiwać jego pozostałe wartości jako odrzuty.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji na temat dekonstrukcji krotek z odrzutami, zobacz [Dekonstrukcja krotek i innych typów](deconstruct.md#deconstructing-tuple-elements-with-discards).

Metoda `Deconstruct` klasy, struktury lub interfejsu umożliwia również pobieranie i dekonstruowanie określonego zestawu danych z obiektu. Można użyć odrzutów, jeśli jesteś zainteresowany pracą tylko z podzbiorem zdekonstruowanych wartości. Poniższy przykład dekonstruuje `Person` obiekt na cztery ciągi (imię i nazwisko, miasto i stan), ale odrzuca nazwisko i stan.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Aby uzyskać więcej informacji na temat dekonstrukcji typów zdefiniowanych przez użytkownika za pomocą odrzutów, zobacz [Dekonstrukcja krotek i innych typów](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Dopasowanie wzoru `switch` do`is`

*Wzorzec odrzutów* może służyć w dopasowaniu wzorca do słów kluczowych [is](language-reference/keywords/is.md) i [switch.](language-reference/keywords/switch.md) Każde wyrażenie zawsze pasuje do wzorca odrzutów.

Poniższy przykład definiuje `ProvidesFormatInfo` metodę, która używa [jest](language-reference/keywords/is.md) instrukcje, <xref:System.IFormatProvider> aby ustalić, czy `null`obiekt zapewnia implementację i sprawdza, czy obiekt jest . Używa również wzorzec odrzutów do obsługi obiektów innych niż null innego typu.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Wywołania metod z parametrami out

Podczas wywoływania `Deconstruct` metody do dekonstrukcji typu zdefiniowanego przez użytkownika (wystąpienie klasy, struktury lub interfejsu), można odrzucić wartości poszczególnych `out` argumentów. Ale można również odrzucić `out` wartość argumentów podczas wywoływania dowolnej metody z out parametru.

Poniższy przykład wywołuje [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) metoda, aby ustalić, czy ciąg reprezentacji daty jest prawidłowy w bieżącej kulturze. Ponieważ przykład dotyczy tylko sprawdzania poprawności ciągu daty, a nie analizowania go `out` w celu wyodrębnienia daty, argument metody jest odrzuceniem.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Samodzielny odrzut

Można użyć autonomicznego odrzucenia, aby wskazać dowolną zmienną, która zostanie zignorowana. W poniższym przykładzie użyto autonomicznego odrzucenia, aby zignorować <xref:System.Threading.Tasks.Task> obiekt zwrócony przez operację asynchroniczną. Ma to wpływ na pomijanie wyjątku, który zgłasza operację, gdy ma zostać ukończona.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Należy `_` zauważyć, że jest to również prawidłowy identyfikator. Gdy używany poza obsługiwanym `_` kontekście, jest traktowany nie jako odrzut, ale jako prawidłowa zmienna. Jeśli identyfikator o `_` nazwie jest już w `_` zakresie, użycie jako autonomicznego odrzucenia może spowodować:

- Przypadkowe modyfikacje wartości zmiennej `_` w zakresie, przypisując jej wartość zamierzonego odrzucenia. Przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Błąd kompilatora za naruszenie bezpieczeństwa typów. Przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Błąd kompilatora CS0136, "Nie można zadeklarować lokalnego lub parametru o nazwie '\_' ' , ponieważ ta nazwa jest używana w otaczającym zakresie lokalnym do definiowania lokalnego lub parametru." Przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Zobacz też

- [Dekonstrukcja krotek i innych typów](deconstruct.md)
- [`is`Słowa kluczowego](language-reference/keywords/is.md)
- [`switch`Słowa kluczowego](language-reference/keywords/switch.md)
