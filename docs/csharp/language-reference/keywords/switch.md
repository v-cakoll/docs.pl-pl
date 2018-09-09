---
title: Instrukcja switch C#
ms.date: 08/14/2018
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
ms.openlocfilehash: 08b63d67b6175d18bee1317cc8908d876fbb4039
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252093"
---
# <a name="switch-c-reference"></a>Switch (odwołanie w C#)

`switch` jest instrukcją zaznaczenia, który wybiera jeden *Przełącz sekcję* do wykonania z listy kandydatów na podstawie dopasowania wzorca z *pasuje do wyrażenia*.

[!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

`switch` Instrukcji jest często używana jako alternatywa [if-else](if-else.md) konstruowania, jeśli pojedyncze wyrażenie jest testowany dla trzech lub więcej warunków. Na przykład następująca `switch` Instrukcja określa, czy zmienna typu `Color` ma jedną z trzech wartości:

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Jest to równoważne do poniższego przykładu, który używa `if` - `else` konstruowania.

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Wyrażenie dopasowania

Wyrażenie dopasowania udostępnia wartość do dopasowywania wzorców w `case` etykiety. Jego składnia jest następująca:

```csharp
   switch (expr)
```

W języku C# 6 wyrażenie dopasowania musi być wyrażeniem, która zwraca wartość z następujących typów:

- [char](char.md).
- [ciąg](string.md).
- [bool](bool.md).
- wartość całkowita, takich jak [int](int.md) lub [długie](long.md).
- [wyliczenia](enum.md) wartość.

Wyrażenie dopasowania, począwszy od języka C# 7.0, może być dowolnym wyrażeniem inną niż null.

## <a name="the-switch-section"></a>Sekcja przełącznika

A `switch` wyciąg zawiera jeden lub więcej sekcji przełączników. Każda sekcja przełącznika zawiera jedną lub więcej *zamierzone, Zapisz etykiety* (etykieta case lub default) następuje jedna lub więcej instrukcji. `switch` Instrukcja może zawierać co najwyżej jedną etykietę domyślną umieszczone w żadnej sekcji przełącznika. W poniższym przykładzie przedstawiono prosty `switch` instrukcję, która zawiera trzy sekcje przełącznika, każdy z nich zawierający dwie instrukcje. Druga sekcja przełącznika zawiera `case 2:` i `case 3:` etykiety.

A `switch` instrukcji może zawierać dowolną liczbę sekcji przełącznika, a każda sekcja może mieć jedną lub więcej etykiet wielkości liter, jak pokazano w poniższym przykładzie. Jednak żadne dwie etykiety mogą zawierać to samo wyrażenie.

[!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Wykonuje sekcji tylko jednego przełącznika w instrukcji switch. C# nie zezwala na wykonywanie kontynuowało z jednej sekcji przełączania do następnej. W związku z tym poniższy kod generuje błąd kompilatora CS0163: "Sterowanie nie może przechodzić od jednej etykiety case (<case label>) do innego."

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

Wymóg ten jest zazwyczaj spełniony przy jawnie zamykania sekcji przełącznika, za pomocą [podziału](break.md), [goto](goto.md), lub [zwracają](return.md) instrukcji. Jednak poniższy kod jest również ważne, ponieważ zapewnia, że formant programu nie może przechodzić do `default` Przełącz sekcję.

[!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Wykonanie listy instrukcji w sekcji przełącznika, etykietę case, która odpowiada wyrażeniu dopasowanie rozpoczyna się od pierwszej instrukcji i przechodzi przez listę instrukcji, zwykle aż do instrukcja skoku, takiej jak `break`, `goto case`, `goto label`, `return`, lub `throw`, zostanie osiągnięty. W tym momencie przekazanie kontroli poza `switch` instrukcji lub do innej etykiety sprawy. A `goto` instrukcji, jeśli jest on używany, musi kontrola jest przekazywana do stałej etykiety. To ograniczenie jest konieczne, ponieważ próby kontrola jest przekazywana do etykiety niestałe może mieć niepożądane skutki uboczne, takie transferowanie formantu do niezamierzonych lokalizacji w kodzie lub tworzenie pętli nieskończonej.

## <a name="case-labels"></a>Etykiety Case

Każda etykieta przypadku określa wzorzec do porównania z wyrażenia dopasowania ( `caseSwitch` zmiennej w poprzednich przykładach). Jeśli są zgodne, kontrola jest przekazywana do sekcji przełącznika, który zawiera **pierwszy** odpowiadających im etykiet wielkości liter. Jeśli nie wzorzec etykietę "case" pasuje do wyrażenia dopasowania, kontrola jest przekazywana do sekcji z `default` etykiety case, jeśli taka istnieje. W przypadku nie `default` przypadku żadnych deklaracji w żadnej sekcji przełącznika są wykonywane, a kontrola jest przekazywana poza `switch` instrukcji.

Instrukcje dotyczące `switch` instrukcji i dopasowywania do wzorca, zobacz [dopasowywania do wzorca z `switch` instrukcji](#pattern) sekcji.

Ponieważ języka C# 6 obsługuje tylko stałe wzorzec i nie zezwala na powtórzenia wartości stałych, etykiet case zdefiniować wartości wzajemnie się wykluczają i tylko jeden wzorzec może być zgodna z wyrażeniem dopasowania. W rezultacie, kolejność, w której `case` instrukcje są wyświetlane, nie ma znaczenia.

W języku C# 7.0, ponieważ inne wzorce są obsługiwane, etykiet case nie muszą definiować wartości wzajemnie się wykluczają i wielu wzorców może odnosić się wyrażenie dopasowania. Ponieważ wykonywane są tylko instrukcje w sekcji przełącznika, który zawiera definicję wzorca pierwszego dopasowania, kolejność, w której `case` instrukcje pojawiają się teraz jest ważne. Jeśli C# wykryje sekcji przełącznika, których instrukcji case instrukcje są równoważne lub są podzbiorem poprzednich instrukcji, generuje błąd kompilatora, CS8120, "przypadku switch została już obsłużona przez poprzednią etykietę case."

W poniższym przykładzie pokazano `switch` instrukcję, która korzysta z rozmaitych wzorców bez wzajemnie się wykluczają. Jeśli przeniesiesz `case 0:` Przełącz sekcję, tak aby nie jest już pierwszej sekcji `switch` instrukcja języka C#, generuje błąd kompilatora, ponieważ liczbą całkowitą, którego wartość jest równa zero jest podzestawem wszystkich liczb całkowitych, czyli wzorca określonego przez `case int val` Instrukcja.

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Można rozwiązać ten problem i wyeliminować ostrzeżenia kompilatora, w jeden z dwóch sposobów:

- Zmieniając ich kolejność sekcji przełączników.

- Przy użyciu < /a name = "kiedy" > po klauzuli</a> w `case` etykiety.

## <a name="the-default-case"></a>`default` Case

`default` Case określa sekcji przełącznika, do wykonania, jeśli wyrażenie dopasowania nie odpowiada żadnej innej `case` etykiety. Jeśli `default` przypadek nie jest obecny i wyrażenie dopasowania nie odpowiada żadnej innej `case` etykiety, przepływem programu przypada za pośrednictwem `switch` instrukcji.

`default` Przypadków mogą być wyświetlane w dowolnej kolejności w `switch` instrukcji. Niezależnie od ich kolejność, w kodzie źródłowym, będzie zawsze oceniana, last, po wszystkich `case` etykiety zostały ocenione.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> Za pomocą dopasowywania do wzorca `switch` — instrukcja

Każdy `case` instrukcja definiuje wzorzec pasujący wyrażenie dopasowania powoduje, że jego zawierającego sekcji przełącznika, do wykonania. Wszystkie wersje języka C# obsługuje wzór stałej. Pozostałe wzorce są obsługiwane, począwszy od języka C# 7.0.

### <a name="constant-pattern"></a>Wzór stałej

Wzór stałej sprawdza, czy wyrażenie dopasowania jest równa określonej stałej. Jego składnia jest następująca:

```csharp
   case constant:
```

gdzie *stałej* jest wartością do testowania. *Stała* może być dowolną z następujących stałych wyrażeń:

- A [bool](bool.md) literału, albo `true` lub `false`.
- Dowolnego całkowitego stałych, takich jak [int](int.md), [długie](long.md), lub [bajt](byte.md).
- Nazwa deklarowanej `const` zmiennej.
- Stała wyliczenia.
- A [char](char.md) literału.
- A [ciąg](string.md) literału.

Stałe wyrażenie jest obliczane w następujący sposób:

- Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.

W poniższym przykładzie użyto wzór stałej, aby ustalić, czy określoną datę w weekendy, pierwszego dnia tygodnia pracy, ostatni dzień tygodnia pracy lub w środku tygodnia pracy. Powoduje ono obliczenie <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwości bieżącego dnia w odniesieniu do składowych aspektów <xref:System.DayOfWeek> wyliczenia.

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

W poniższym przykładzie użyto wzór stałej do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje maszyny do automatycznego kawy.

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Wpisz wzór

Wpisz wzór umożliwia ocenę zwięzły typ i konwersji. Gdy jest używane z `switch` instrukcję do realizacji dopasowania do wzorca, jego testuje, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu. Jego składnia jest następująca:

```csharp
   case type varname
```

gdzie *typu* jest nazwą typu, do której wynik *expr* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr*jest konwertowany, jeśli dopasowanie się powiedzie.

`case` Wyrażenie jest `true` jeśli spełniony jest dowolny z następujących czynności:

- *wyrażenie* to wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*. Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.

- *wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*. *Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji typu. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

Jeśli wyrażenie case ma wartość true, *nazwa_zmiennej* jest zdecydowanie przypisana, a ma zakres lokalny w ramach tej sekcji przełącznika.

Należy pamiętać, że `null` jest niezgodny z typem. Aby dopasować `null`, użyj następującego `case` etykiety:

```csharp
case null:
```

W poniższym przykładzie użyto wzorca typu, aby podać informacje o różnych rodzajów typów kolekcji.

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób. Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null` lub do wykonywania powtarzających rzutowania.

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" /> `case` Instrukcji i `when` — klauzula

Uruchamianie przy użyciu języka C# 7.0, ponieważ instrukcji case nie muszą być wzajemnie się wykluczają, możesz dodać `when` klauzulę, aby określić dodatkowy warunek muszą być spełnione dla instrukcji case na wartość true. `when` Klauzuli może być dowolne wyrażenie zwracające wartość logiczną.

W poniższym przykładzie zdefiniowano podstawowej `Shape` klasy `Rectangle` klasę pochodzącą od `Shape`, a `Square` klasę pochodzącą od `Rectangle`. Używa ona `when` klauzuli, aby upewnić się, że `ShowShapeInfo` traktuje `Rectangle` obiekt, który został przypisany równy długości i szerokości jako `Square` nawet, jeśli nie utworzono wystąpienia jako `Square` obiektu. Metoda nie jest podejmowana próba wyświetlenia informacji o obiekt, który jest `null` lub kształtu, w których obszar jest równa zero.

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Należy pamiętać, że `when` klauzuli w przykładzie, który próbuje testów czy `Shape` obiekt jest `null` nie jest wykonywane. Wzorzec poprawnego typu do testowania `null` jest `case null:`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [instrukcji switch](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) w [specyfikacji języka C#](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [if-else](if-else.md)
- [Dopasowanie do wzorca](../../pattern-matching.md)