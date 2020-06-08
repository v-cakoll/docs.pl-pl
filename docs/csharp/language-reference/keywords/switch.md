---
title: Instrukcja Switch języka C#
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 9335399be2d4909a02fecbf2959c6f5608664732
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493672"
---
# <a name="switch-c-reference"></a>Switch (odwołanie w C#)

Ten artykuł dotyczy `switch` instrukcji. Aby uzyskać informacje na temat `switch` wyrażenia (wprowadzonego w języku C# 8,0), zobacz artykuł dotyczący [ `switch` wyrażeń](../operators/switch-expression.md) w sekcji [wyrażenia i operatory](../operators/index.md) .

`switch`jest instrukcją wyboru, która wybiera pojedynczy *przełącznik* , który ma zostać wykonany z listy kandydatów na podstawie dopasowania wzorca z *wyrażeniem Match*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

`switch`Instrukcja jest często używana jako alternatywa dla konstrukcji [if-else](if-else.md) , jeśli pojedyncze wyrażenie jest testowane w oparciu o trzy lub więcej warunków. Na przykład Poniższa `switch` instrukcja określa, czy zmienna typu `Color` ma jedną z trzech wartości:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Jest to odpowiednik poniższego przykładu korzystającego z `if` - `else` konstrukcji.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Wyrażenie dopasowania

Wyrażenie Match zawiera wartość do dopasowania względem wzorców w `case` etykietach. Jego składnia to:

```csharp
   switch (expr)
```

W języku C# 6 i wcześniejszych wyrażenie Match musi być wyrażeniem zwracającym wartość następujących typów:

- [znak](../builtin-types/char.md).
- [ciąg](../builtin-types/reference-types.md).
- wartość [logiczna](../builtin-types/bool.md).
- wartość [całkowita](../builtin-types/integral-numeric-types.md) , taka jak `int` lub `long` .
- wartość [wyliczenia](../builtin-types/enum.md) .

Począwszy od języka C# 7,0 wyrażenie Match może być dowolnym wyrażeniem o wartości innej niż null.

## <a name="the-switch-section"></a>Sekcja Switch

`switch`Instrukcja zawiera jedną lub więcej sekcji przełączników. Każda sekcja przełącznika zawiera jedną lub więcej *etykiet przypadków* (literę lub etykietę domyślną), po której następuje jedna lub więcej instrukcji. `switch`Instrukcja może zawierać co najwyżej jedną etykietę domyślną umieszczoną w dowolnej sekcji Switch. Poniższy przykład pokazuje prostą `switch` instrukcję, która ma trzy sekcje przełączników, z których każda zawiera dwie instrukcje. Druga sekcja Switch zawiera `case 2:` `case 3:` etykiety i.

`switch`Instrukcja może zawierać dowolną liczbę sekcji przełączników, a Każda sekcja może mieć jedną lub więcej etykiet wielkości liter, jak pokazano w poniższym przykładzie. Jednak żadne dwie etykiety wielkości liter nie mogą zawierać tego samego wyrażenia.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

W instrukcji switch jest wykonywana tylko jedna sekcja Switch. Język C# nie zezwala na kontynuowanie wykonywania z jednej sekcji przełącznika do następnej. W związku z tym Poniższy kod generuje błąd kompilatora, CS0163: "kontrolka nie może przechodzić z jednej etykiety case ( \<case label> ) do innej".

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

To wymaganie jest zwykle spełnione przez jawne opuszczenie sekcji Switch za pomocą instrukcji [Break](break.md), [goto](goto.md)lub [Return](return.md) . Jednak następujący kod jest również prawidłowy, ponieważ zapewnia, że Kontrolka programu nie może przechodzić do `default` sekcji Switch.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Wykonanie listy instrukcji w sekcji Switch z etykietą Case, która pasuje do wyrażenia Match rozpoczyna się od pierwszej instrukcji i przechodzi przez listę instrukcji, zwykle do momentu osiągnięcia instrukcji skoku, takiej jak,,,, `break` `goto case` `goto label` `return` lub `throw` . W tym momencie formant jest transferowany poza `switch` instrukcją lub inną etykietą przypadku. `goto`Instrukcja, jeśli jest używana, musi przekazywać kontrolę do etykiety stałej. To ograniczenie jest konieczne, ponieważ próba przetransferowania kontroli do etykiety niestałej może mieć niepożądane efekty uboczne, takie przeniesienie kontroli do niezamierzonej lokalizacji w kodzie lub utworzenie pętli nieskończonej.

## <a name="case-labels"></a>Etykiety przypadku

Każda etykieta przypadku określa wzorzec do porównania z wyrażeniem dopasowania ( `caseSwitch` zmienna w poprzednich przykładach). Jeśli są one zgodne, sterowanie jest przekazywane do sekcji Switch, która zawiera **pierwszą** pasującą etykietę case. Jeśli żaden wzorzec etykiety case nie jest zgodny z wyrażeniem Match, formant jest przenoszony do sekcji z `default` etykietą przypadku, jeśli istnieje. Jeśli nie ma żadnego `default` przypadku, nie są wykonywane żadne instrukcje, a kontrolka jest transferowana poza `switch` instrukcją.

Aby uzyskać informacje na temat `switch` dopasowania do instrukcji i wzorca, zobacz Zgodność [wzorca z sekcją `switch` instrukcji](#pattern-matching with-the-switch-statement) .

Ponieważ C# 6 obsługuje tylko wzorce stałe i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości, a tylko jeden wzorzec może być zgodny z wyrażeniem Match. W związku z tym kolejność, w której `case` wyświetlane są instrukcje, jest nieważna.

W języku C# 7,0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczających się wartości, a wiele wzorców może pasować do wyrażenia Match. Ponieważ są wykonywane tylko instrukcje w pierwszej sekcji przełącznika, które zawiera pasujący wzorzec, kolejność, w której są `case` wyświetlane instrukcje, jest teraz ważna. Jeśli w języku C# wykryje sekcja Switch, której instrukcja "Case" lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120 "przypadek przełączania został już obsłużony w poprzednim przypadku".

Poniższy przykład ilustruje `switch` instrukcję, która używa różnych niewzajemnie wyłącznych wzorców. Jeśli przesuniesz `case 0:` sekcję Switch tak, aby nie była już pierwszą sekcją w `switch` instrukcji, w języku C# zostanie wygenerowany błąd kompilatora, ponieważ liczba całkowita, której wartością jest zero, jest podzbiorem wszystkich liczb całkowitych, które jest wzorcem zdefiniowanym przez `case int val` instrukcję.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Możesz rozwiązać ten problem i wyeliminować Ostrzeżenie kompilatora na jeden z dwóch sposobów:

- Zmieniając kolejność sekcji Switch.

- Za pomocą [klauzuli when](#the-case-statement-and-the-when-clause) w `case` etykiecie.

## <a name="the-default-case"></a>`default`Wielkość liter

`default`Przypadek określa sekcję Switch, która ma zostać wykonana, jeśli wyrażenie Match nie jest zgodne z żadną inną `case` etykietą. Jeśli `default` przypadek nie istnieje i wyrażenie Match nie pasuje do żadnej innej `case` etykiety, przepływ programu przechodzą przez `switch` instrukcję.

`default`Przypadek może pojawić się w dowolnej kolejności w `switch` instrukcji. Bez względu na jego kolejność w kodzie źródłowym jest zawsze Szacowana jako Ostatnia, po `case` ocenie wszystkich etykiet.

## <a name="pattern-matching-with-the-switch-statement"></a>Dopasowanie wzorca do `switch` instrukcji

Każda `case` instrukcja definiuje wzorzec, który jest zgodny z wyrażeniem Match, powoduje, że jego sekcja Switch zostanie wykonana. Wszystkie wersje języka C# obsługują stałe wzorce. Pozostałe wzorce są obsługiwane począwszy od języka C# 7,0.

### <a name="constant-pattern"></a>Wzorzec stałej

Wzorzec stałej testuje, czy wyrażenie dopasowania jest równe określonej stałej. Jego składnia to:

```csharp
   case constant:
```

gdzie *stała* jest wartością do przetestowania. *stała* może być dowolnym z następujących wyrażeń stałych:

- Literał [bool](../builtin-types/bool.md) : `true` lub `false` .
- Dowolna stała [całkowita](../builtin-types/integral-numeric-types.md) , taka jak `int` , a `long` lub `byte` .
- Nazwa zadeklarowanej `const` zmiennej.
- Stała wyliczenia.
- Literał [znakowy](../builtin-types/char.md) .
- Literał [ciągu](../builtin-types/reference-types.md) .

Wyrażenie stałe jest oceniane w następujący sposób:

- Jeśli *wyrażenie* i *stała* są typami całkowitymi, operator równości języka C# określa, czy wyrażenie zwróci wartość `true` (to znaczy czy `expr == constant` ).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody static [obiektu. Equals (wyrażenie, stała)](xref:System.Object.Equals(System.Object,System.Object)) .

W poniższym przykładzie za pomocą wzorca stałego można określić, czy konkretna data to weekend, pierwszy dzień tygodnia pracy, ostatni dzień tygodnia pracy lub środek tygodnia pracy. Oblicza <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> Właściwość bieżącego dnia względem elementów członkowskich <xref:System.DayOfWeek> wyliczenia.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Poniższy przykład używa wzorca stałego do obsługi danych wejściowych użytkownika w aplikacji konsolowej, która symuluje automatyczną maszynę Kawową.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Wzorzec typu

Wzorzec typu umożliwia obliczanie i konwersję zwięzłego typu. Gdy jest używany z `switch` instrukcją do wykonywania dopasowania do wzorca, sprawdza, czy wyrażenie może być konwertowane do określonego typu i, jeśli to możliwe, rzutuje go na zmienną tego typu. Jego składnia to:

```csharp
   case type varname
```

Where *Type* jest nazwą typu, do którego zostanie przekonwertowany wynik *wyrażenia* , a *nazwa_zmiennej* jest obiektem, do którego zostanie przekonwertowany wynik *wyrażenia* , jeśli dopasowanie się powiedzie. Typ "czas kompilacji" *wyrażenia* może być parametrem typu ogólnego, rozpoczynając od języka C# 7,1.

`case`Wyrażenie ma `true` wartość PRAWDA:

- *wyrażenie* jest wystąpieniem tego samego typu co *Typ*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od *typu*. Innymi słowy, wynik *wyrażenia* może być rzutowany na wystąpienie *typu*.

- *wyrażenie* ma typ czasu kompilacji, który jest klasą bazową *typu*, a *wyrażenie* ma typ środowiska uruchomieniowego, który jest *typem* lub pochodzi od *typu*. *Typ czasu kompilacji* zmiennej to typ zmiennej, zgodnie z definicją w deklaracji typu. *Typ środowiska uruchomieniowego* zmiennej to typ wystąpienia, które jest przypisane do tej zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje interfejs *typu* .

Jeśli wyrażenie CASE ma wartość true, właściwość *nazwa_zmiennej* jest ostatecznie przypisana i ma zakres lokalny tylko w sekcji Switch.

Zwróć uwagę, że `null` nie pasuje do typu. Aby dopasować do `null` , należy użyć następującej `case` etykiety:

```csharp
case null:
```

Poniższy przykład używa wzorca typu, aby podać informacje dotyczące różnych rodzajów typów kolekcji.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Zamiast `object` , można utworzyć metodę rodzajową przy użyciu typu kolekcji jako parametru typu, jak pokazano w poniższym kodzie:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Wersja ogólna różni się od pierwszej próbki na dwa sposoby. Po pierwsze nie można użyć `null` przypadku. Nie można użyć żadnego ze stałych przypadków, ponieważ kompilator nie może konwertować dowolnego dowolnego typu `T` do dowolnego typu innego niż `object` . Co było miało `default` teraz testy o wartości innej niż null `object` . Oznacza to, że `default` testy przypadku tylko dla `null` .

Bez dopasowania do wzorca ten kod może być zapisany w następujący sposób. Użycie dopasowania wzorca typu daje bardziej zwarty, czytelny kod, eliminując konieczność sprawdzenia, czy wynik konwersji jest `null` lub aby wykonać powtarzające się rzutowania.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case`Instrukcja i `when` klauzula

Począwszy od języka C# 7,0, ponieważ instrukcje Case nie muszą się wzajemnie wykluczać, można dodać `when` klauzulę, aby określić dodatkowy warunek, który musi być spełniony dla instrukcji case, aby obliczyć wartość true. `when`Klauzula może być dowolnym wyrażeniem zwracającym wartość logiczną.

W poniższym przykładzie zdefiniowano klasę bazową `Shape` , `Rectangle` Klasa, która pochodzi od `Shape` klasy, i `Square` Klasa, która pochodzi od `Rectangle` . Używa klauzuli, `when` Aby zapewnić, że `ShowShapeInfo` traktuje `Rectangle` obiekt, który ma przypisaną taką samą długość i szerokość, `Square` nawet jeśli nie został skonkretyzowany jako `Square` obiekt. Metoda nie próbuje wyświetlić informacji o obiekcie `null` lub kształcie, którego obszar jest równy zero.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Należy zauważyć, że `when` klauzula w przykładzie, która próbuje sprawdzić, czy `Shape` obiekt `null` nie jest wykonywany. Poprawny wzorzec typu do przetestowania dla elementu `null` is `case null:` .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [instrukcja SWITCH](~/_csharplang/spec/statements.md#the-switch-statement) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [if-else](if-else.md)
- [Dopasowanie wzorca](../../pattern-matching.md)
