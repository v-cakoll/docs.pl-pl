---
title: Instrukcja przełączania języka C#
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
ms.openlocfilehash: 49b3836f17e91ae8de10d68e97fd662aae80d1ff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249321"
---
# <a name="switch-c-reference"></a>przełącznik (odwołanie C#)

Ten artykuł `switch` obejmuje instrukcję. Aby uzyskać `switch` informacje na temat wyrażenia (wprowadzone w języku C# 8.0), zobacz artykuł na [ `switch` wyrażenia](../operators/switch-expression.md) w [wyrażeń i operatorów](../operators/index.md) sekcji.

`switch`jest instrukcją wyboru, która wybiera *sekcję* pojedynczego przełącznika do wykonania z listy kandydatów na podstawie dopasowania wzorca z *wyrażeniem dopasowania*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Instrukcja `switch` jest często używana jako alternatywa dla [konstrukcji if-else,](if-else.md) jeśli pojedyncze wyrażenie jest testowane pod względem trzech lub więcej warunków. Na przykład następująca `switch` instrukcja określa, `Color` czy zmienna typu ma jedną z trzech wartości:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Jest to równoważne z poniższym `if` - `else` przykładem, który używa konstrukcji.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Wyrażenie dopasowania

Wyrażenie dopasowania zawiera wartość dopasowaną do `case` wzorców w etykietach. Jego składnia to:

```csharp
   switch (expr)
```

W języku C# 6 i wcześniej wyrażenie dopasowania musi być wyrażeniem, które zwraca wartość następujących typów:

- [char](../builtin-types/char.md).
- [ciąg znaków](../builtin-types/reference-types.md).
- [bool](../builtin-types/bool.md).
- wartości [integralnej,](../builtin-types/integral-numeric-types.md) takiej `int` jak `long`lub .
- wartości [wyliczenia.](../builtin-types/enum.md)

Począwszy od C# 7.0 wyrażenie dopasowania może być dowolne wyrażenie inne niż null.

## <a name="the-switch-section"></a>Sekcja przełącznika

Instrukcja `switch` zawiera co najmniej jedną sekcję przełącznika. Każda sekcja przełącznika zawiera jedną lub więcej *etykiet przypadków* (przypadek lub etykietę domyślną), po której następuje co najmniej jedna instrukcja. Instrukcja `switch` może zawierać co najwyżej jedną domyślną etykietę umieszczona w dowolnej sekcji przełącznika. W poniższym przykładzie przedstawiono prostą `switch` instrukcję, która ma trzy sekcje przełącznika, z których każda zawiera dwie instrukcje. Druga sekcja przełącznika `case 2:` `case 3:` zawiera i etykiety.

Instrukcja `switch` może zawierać dowolną liczbę sekcji przełącznika, a każda sekcja może mieć jedną lub więcej etykiet przypadków, jak pokazano w poniższym przykładzie. Jednak żadne dwie etykiety przypadków nie mogą zawierać tego samego wyrażenia.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Wykonuje tylko jedną sekcję przełącznika w instrukcji switch. C# nie zezwala na wykonywanie, aby kontynuować z jednej sekcji przełącznika do następnego. Z tego powodu następujący kod generuje błąd kompilatora, CS0163: "Kontrola\<nie może przechodzić z jednej etykiety sprawy (etykieta sprawy>) do innej."

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

To wymaganie jest zwykle spełnione przez jawne wyjście z sekcji przełącznika za pomocą [break](break.md), [goto](goto.md)lub [return](return.md) instrukcji. Jednak poniższy kod jest również prawidłowy, ponieważ zapewnia, że formant programu nie może spaść do sekcji przełącznika. `default`

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Wykonanie listy instrukcji w sekcji przełącznika z etykietą sprawy, która pasuje do wyrażenia dopasowania, rozpoczyna się od pierwszej instrukcji `break` `goto case`i `goto label` `return`przebiega `throw`przez listę instrukcji, zazwyczaj do momentu osiągnięcia instrukcji skoku, takiej jak , , , lub ,. W tym momencie kontrola jest `switch` przenoszona poza instrukcję lub do innej etykiety sprawy. Instrukcja, `goto` jeśli jest używana, należy przenieść formant do stałej etykiety. To ograniczenie jest konieczne, ponieważ próba przeniesienia kontroli do etykiety niestanowej może mieć niepożądane skutki uboczne, takie jak przenoszenie kontroli do niezamierzonelokalnie w kodzie lub tworzenie nieskończonej pętli.

## <a name="case-labels"></a>Etykiety etui

Każda etykieta sprawy określa wzorzec do `caseSwitch` porównania z wyrażeniem dopasowania (zmienną w poprzednich przykładach). Jeśli są zgodne, formant jest przenoszony do sekcji przełącznika, która zawiera **pierwszą** etykietę pasujące sprawy. Jeśli żaden wzorzec etykiety sprawy nie pasuje do wyrażenia `default` dopasowania, formant jest przenoszony do sekcji z etykietą sprawy, jeśli istnieje. Jeśli nie ma `default` przypadku, nie instrukcje w dowolnej sekcji przełącznik są `switch` wykonywane i kontroli jest przenoszony poza instrukcję.

Aby uzyskać `switch` informacje na temat dopasowywania instrukcji i wzorca, zobacz [Dopasowanie wzorca z sekcją `switch` instrukcji.](#pattern)

Ponieważ C# 6 obsługuje tylko stały wzorzec i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości, a tylko jeden wzorzec może odpowiadać wyrażeniu dopasowania. W rezultacie kolejność, w `case` której pojawiają się instrukcje, jest nieistotna.

W języku C# 7.0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczające się wartości i wiele wzorców może odpowiadać wyrażenie dopasowania. Ponieważ wykonywane są tylko instrukcje w pierwszej sekcji przełącznika, `case` która zawiera pasujący wzorzec, kolejność, w której pojawiają się instrukcje, jest teraz ważna. Jeśli C# wykrywa sekcji switch, którego case instrukcji lub instrukcji są równoważne lub są podzbiory poprzednich instrukcji, generuje błąd kompilatora, CS8120, "Przypadek przełącznika został już obsłużony przez poprzedni przypadek."

Poniższy przykład ilustruje instrukcję, `switch` która używa różnych wzorców nie wykluczają się wzajemnie. Jeśli przeniesiesz `case 0:` przełączyć sekcji tak, że nie `switch` jest już pierwszą sekcję w instrukcji, C# generuje błąd kompilatora, ponieważ liczba całkowita, której `case int val` wartość wynosi zero jest podzbiorem wszystkich całkowitej liczby, który jest wzorzec zdefiniowany przez instrukcję.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Można rozwiązać ten problem i wyeliminować ostrzeżenie kompilatora na jeden z dwóch sposobów:

- Zmieniając kolejność sekcji przełącznika.

- Za pomocą [when klauzuli](#when) na etykiecie. `case`

## <a name="the-default-case"></a>Sprawa `default`

Przypadek `default` określa sekcję switch do wykonania, jeśli wyrażenie dopasowania `case` nie pasuje do żadnej innej etykiety. Jeśli `default` przypadek nie jest obecny, a wyrażenie dopasowania `case` nie pasuje do `switch` żadnej innej etykiety, przepływ programu przechodzi przez instrukcję.

Sprawa `default` może pojawić się w `switch` dowolnej kolejności w instrukcji. Niezależnie od jego kolejności w kodzie źródłowym, zawsze `case` jest oceniane jako ostatni, po wszystkie etykiety zostały ocenione.

## <a name="pattern-matching-with-the-switch-statement"></a><a name="pattern" />Dopasowanie wzorca `switch` do instrukcji

Każda `case` instrukcja definiuje wzorzec, który, jeśli pasuje do wyrażenia dopasowania, powoduje, że jego sekcja przełączania zawierająca ma zostać wykonana. Wszystkie wersje języka C# obsługują stały wzorzec. Pozostałe wzorce są obsługiwane począwszy od języka C# 7.0.

### <a name="constant-pattern"></a>Stały wzór

Wzorzec stały sprawdza, czy wyrażenie dopasowania jest równe określonej stałej. Jego składnia to:

```csharp
   case constant:
```

gdzie *stała* jest wartością, dla której należy testować. *stała* może być dowolną z następujących wyrażeń stałych:

- [Bool](../builtin-types/bool.md) dosłowny: `true` `false`albo lub .
- Każda stała [integralna,](../builtin-types/integral-numeric-types.md) `int`taka `long`jak `byte`, a lub .
- Nazwa zadeklarowanej `const` zmiennej.
- Stała wyliczenia.
- Char [char](../builtin-types/char.md) dosłowny.
- Literał [ciągu.](../builtin-types/reference-types.md)

Wyrażenie stałe jest oceniane w następujący sposób:

- Jeśli *expr* i *stała* są typami integralnymi, operator `true` równości języka C# określa, czy wyrażenie zwraca (czyli, czy). `expr == constant`

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody [statycznej Object.Equals(expr, constant).](xref:System.Object.Equals(System.Object,System.Object))

W poniższym przykładzie użyto stałego wzorca, aby określić, czy określona data to weekend, pierwszy dzień tygodnia roboczego, ostatni dzień tygodnia roboczego lub środek tygodnia roboczego. Ocenia <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwość bieżącego dnia względem członków <xref:System.DayOfWeek> wyliczenia.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

W poniższym przykładzie użyto stałego wzorca do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje automatyczny ekspres do kawy.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Wzór typu

Wzorzec typu umożliwia zwięzłą ocenę typu i konwersję. W przypadku `switch` użycia z instrukcją do wykonywania dopasowania wzorca, sprawdza, czy wyrażenie może być konwertowane na określony typ i, jeśli może to być, rzutuje go do zmiennej tego typu. Jego składnia to:

```csharp
   case type varname
```

gdzie *typ* jest nazwą typu, na który ma zostać przekonwertowany wynik *expr,* a *nazwa warna* jest obiektem, na który zostanie przekonwertowany wynik *expr,* jeśli dopasowanie zakończy się pomyślnie. Typ *expr* w czasie kompilacji może być parametrem typu ogólnego, począwszy od języka C# 7.1.

Wyrażenie `case` jest, `true` jeśli którykolwiek z następujących jest true:

- *expr* jest wystąpieniem tego samego typu co *typ*.

- *expr* jest wystąpieniem typu, który pochodzi od *typu*. Innymi słowy, wynik *expr* może być upcast do wystąpienia *typu*.

- *expr* ma typ czasu kompilacji, który jest klasą podstawową *typu,* a *expr* ma typ środowiska uruchomieniowego, który jest *typem* lub jest pochodną *typu*. *Typ zmiennej w czasie kompilacji* jest typem zmiennej zdefiniowanym w deklaracji typu. *Typ środowiska wykonawczego* zmiennej jest typem wystąpienia przypisanego do tej zmiennej.

- *expr* jest wystąpieniem typu, który implementuje interfejs *typu.*

Jeśli wyrażenie sprawy jest prawdziwe, *varname* jest zdecydowanie przypisany i ma zakres lokalny tylko w sekcji przełącznika.

Należy `null` zauważyć, że nie pasuje do typu. Aby dopasować program `null`, `case` należy użyć następującej etykiety:

```csharp
case null:
```

W poniższym przykładzie użyto wzorca typu, aby zapewnić informacje o różnych typach kolekcji.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Zamiast `object`, można zrobić metodę rodzajową, przy użyciu typu kolekcji jako parametr typu, jak pokazano w poniższym kodzie:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Wersja ogólna różni się od pierwszej próbki na dwa sposoby. Po pierwsze, nie można `null` użyć przypadku. Nie można użyć żadnego stałego przypadku, ponieważ kompilator `T` nie może `object`przekonwertować dowolnego typu na dowolny typ inny niż . Co było `default` w przypadku teraz testy `object`dla non-null . Oznacza to, `default` że `null`testy przypadku tylko dla .

Bez dopasowywania wzorców ten kod może być zapisywany w następujący sposób. Użycie dopasowywania wzorca typu powoduje uzyskanie bardziej kompaktowego, czytelnego kodu, eliminując konieczność sprawdzenia, czy wynikiem konwersji jest `null` a lub wykonywanie powtarzających się rzutowania.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><a name="when" />Oświadczenie `case` i `when` klauzula

Począwszy od języka C# 7.0, ponieważ case instrukcje `when` nie muszą być wzajemnie wykluczają się, można dodać klauzuli, aby określić dodatkowy warunek, który musi być spełniony dla case instrukcji do oceny true. Klauzula `when` może być dowolnym wyrażeniem, które zwraca wartość logiczną.

Poniższy przykład definiuje `Shape` klasę `Rectangle` podstawową, klasę, `Shape`która `Square` wywodzi `Rectangle`się z , i klasę, która pochodzi od . Używa klauzuli, `when` `ShowShapeInfo` aby upewnić się, że traktuje `Rectangle` obiekt, który został przypisany równe długości i szerokości jako `Square` `Square` nawet jeśli nie został sytuowany jako obiekt. Metoda nie próbuje wyświetlić informacji o obiekcie, `null` który jest lub kształt, którego obszar wynosi zero.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Należy zauważyć, że klauzula `when` w przykładzie, który próbuje sprawdzić, czy `Shape` obiekt nie jest `null` wykonywany. Prawidłowy wzorzec typu `null` `case null:`do przetestowania dla a jest .

## <a name="c-language-specification"></a>specyfikacja języka C#

For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [if-else](if-else.md)
- [Dopasowywanie wzoru](../../pattern-matching.md)
