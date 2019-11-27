---
title: C#Switch, instrukcja
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
ms.openlocfilehash: 012fa5b4d5f39b4dfa4d1c77bc3d6fbe181e78a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428487"
---
# <a name="switch-c-reference"></a>przełącznik (C# odwołanie)

`switch` jest instrukcją wyboru, która wybiera pojedynczy *przełącznik* , który ma zostać wykonany z listy kandydatów na podstawie dopasowania wzorca z *wyrażeniem Match*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Instrukcja `switch` jest często używana jako alternatywa dla konstrukcji [if-else](if-else.md) , jeśli pojedyncze wyrażenie jest testowane w oparciu o trzy lub więcej warunków. Na przykład następująca instrukcja `switch` określa, czy zmienna typu `Color` ma jedną z trzech wartości:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Jest to odpowiednik poniższego przykładu korzystającego z `if`-`else` konstrukcja.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Wyrażenie dopasowania

Wyrażenie Match zawiera wartość do dopasowania względem wzorców w etykietach `case`. Jego składnia to:

```csharp
   switch (expr)
```

W C# 6 i wcześniejszych wyrażenia dopasowania musi być wyrażeniem zwracającym wartość następujących typów:

- [znak](../builtin-types/char.md).
- [ciąg](../builtin-types/reference-types.md).
- wartość [logiczna](bool.md).
- wartość [całkowita](../builtin-types/integral-numeric-types.md) , taka jak `int` lub `long`.
- wartość [wyliczenia](enum.md) .

Począwszy od C# 7,0, wyrażenie dopasowania może być dowolnym wyrażeniem o wartości innej niż null.

## <a name="the-switch-section"></a>Sekcja Switch

Instrukcja `switch` zawiera jedną lub więcej sekcji przełączników. Każda sekcja przełącznika zawiera jedną lub więcej *etykiet przypadków* (literę lub etykietę domyślną), po której następuje jedna lub więcej instrukcji. Instrukcja `switch` może zawierać co najwyżej jedną etykietę domyślną umieszczoną w dowolnej sekcji Switch. Poniższy przykład pokazuje prostą instrukcję `switch`, która ma trzy sekcje przełączników, z których każda zawiera dwie instrukcje. Druga sekcja Switch zawiera etykiety `case 2:` i `case 3:`.

Instrukcja `switch` może zawierać dowolną liczbę sekcji przełączników, a Każda sekcja może mieć jedną lub więcej etykiet wielkości liter, jak pokazano w poniższym przykładzie. Jednak żadne dwie etykiety wielkości liter nie mogą zawierać tego samego wyrażenia.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

W instrukcji switch jest wykonywana tylko jedna sekcja Switch. C#nie zezwala na kontynuowanie wykonywania z jednej sekcji przełącznika do następnej. W związku z tym Poniższy kod generuje błąd kompilatora, CS0163: "kontrolka nie może przechodzić z jednej etykiety case (\<etykieta przypadku >) do innej".

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

To wymaganie jest zwykle spełnione przez jawne opuszczenie sekcji Switch za pomocą instrukcji [Break](break.md), [goto](goto.md)lub [Return](return.md) . Jednak następujący kod jest również prawidłowy, ponieważ gwarantuje, że formant programu nie przechodzi do sekcji przełącznika `default`.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Wykonanie listy instrukcji w sekcji Switch z etykietą Case, która pasuje do wyrażenia Match rozpoczyna się od pierwszej instrukcji i przechodzi przez listę instrukcji, zwykle do momentu osiągnięcia instrukcji skoku, takiej jak `break`, `goto case`, `goto label`, `return`lub `throw`. W tym momencie kontrola jest przekazywana poza instrukcją `switch` lub do innej etykiety case. Instrukcja `goto`, jeśli jest używana, musi przekazywać kontrolę do stałej etykiety. To ograniczenie jest konieczne, ponieważ próba przetransferowania kontroli do etykiety niestałej może mieć niepożądane efekty uboczne, takie przeniesienie kontroli do niezamierzonej lokalizacji w kodzie lub utworzenie pętli nieskończonej.

## <a name="case-labels"></a>Etykiety przypadku

Każda etykieta przypadku określa wzorzec do porównania z wyrażeniem dopasowania (zmienna `caseSwitch` w poprzednich przykładach). Jeśli są one zgodne, sterowanie jest przekazywane do sekcji Switch, która zawiera **pierwszą** pasującą etykietę case. Jeśli żaden wzorzec etykiety case nie jest zgodny z wyrażeniem Match, formant jest przenoszony do sekcji z etykietą przypadku `default`, jeśli istnieje. Jeśli nie ma `default`j wielkości liter, nie są wykonywane żadne instrukcje w żadnej sekcji Switch, a kontrolka jest transferowana poza instrukcją `switch`.

Aby uzyskać informacje na temat instrukcji `switch` i dopasowania do wzorca, zobacz Zgodność [wzorców z sekcją `switch` instrukcji](#pattern) .

Ponieważ C# 6 obsługuje tylko wzorce stałe i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości, a tylko jeden wzorzec może być zgodny z wyrażeniem Match. W związku z tym kolejność, w której pojawiają się instrukcje `case`, jest nieważna.

W C# 7,0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczających się wartości, a wiele wzorców może pasować do wyrażenia Match. Ponieważ są wykonywane tylko instrukcje w pierwszej sekcji przełącznika, które zawiera pasujący wzorzec, kolejność, w której pojawiają się instrukcje `case`, jest teraz ważna. Jeśli C# program wykryje sekcję Switch, której instrukcją Case lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120, "przypadek przełączania został już obsłużony przez poprzednią literę".

Poniższy przykład ilustruje instrukcję `switch`, która używa różnych niewzajemnie wykluczających się wzorców. Jeśli przeniesiesz sekcję Switch `case 0:` tak, aby nie była już pierwszą sekcją w instrukcji `switch`, program C# generuje błąd kompilatora, ponieważ liczba całkowita, której wartością jest zero, jest podzbiorem wszystkich liczb całkowitych, które jest wzorcem zdefiniowanym przez instrukcję `case int val`.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Możesz rozwiązać ten problem i wyeliminować Ostrzeżenie kompilatora na jeden z dwóch sposobów:

- Zmieniając kolejność sekcji Switch.

- Za pomocą [klauzuli when](#when) w etykiecie `case`.

## <a name="the-default-case"></a>`default` przypadku

`default` Case określa sekcję Switch, która ma zostać wykonana, jeśli wyrażenie Match nie pasuje do żadnej innej etykiety `case`. Jeśli `default` przypadku nie istnieje i wyrażenie Match nie jest zgodne z żadną inną etykietą `case`, przepływ programu odbywa się za pomocą instrukcji `switch`.

Przypadek `default` może występować w dowolnej kolejności w instrukcji `switch`. Bez względu na jego kolejność w kodzie źródłowym jest zawsze Szacowana jako Ostatnia, po ocenie wszystkich etykiet `case`.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> dopasowywania do wzorca przy użyciu instrukcji `switch`

Każda instrukcja `case` definiuje wzorzec, który jest zgodny z wyrażeniem Match, powoduje, że jego sekcja Switch zostanie wykonana. Wszystkie wersje programu C# obsługują stałe wzorce. Pozostałe wzorce są obsługiwane począwszy od C# 7,0.

### <a name="constant-pattern"></a>Wzorzec stałej

Wzorzec stałej testuje, czy wyrażenie dopasowania jest równe określonej stałej. Jego składnia to:

```csharp
   case constant:
```

gdzie *stała* jest wartością do przetestowania. *stała* może być dowolnym z następujących wyrażeń stałych:

- Literał [bool](bool.md) , `true` lub `false`.
- Dowolna stała [całkowita](../builtin-types/integral-numeric-types.md) , taka jak `int`, `long`lub `byte`.
- Nazwa zadeklarowanej zmiennej `const`.
- Stała wyliczenia.
- Literał [znakowy](../builtin-types/char.md) .
- Literał [ciągu](../builtin-types/reference-types.md) .

Wyrażenie stałe jest oceniane w następujący sposób:

- Jeśli *wyrażenie* i *stała* są typami całkowitymi, C# operator równości określa, czy wyrażenie zwróci `true` (to znaczy czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody static [obiektu. Equals (wyrażenie, stała)](xref:System.Object.Equals(System.Object,System.Object)) .

W poniższym przykładzie za pomocą wzorca stałego można określić, czy konkretna data to weekend, pierwszy dzień tygodnia pracy, ostatni dzień tygodnia pracy lub środek tygodnia pracy. Oblicza Właściwość <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> bieżącego dnia względem elementów członkowskich wyliczenia <xref:System.DayOfWeek>.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Poniższy przykład używa wzorca stałego do obsługi danych wejściowych użytkownika w aplikacji konsolowej, która symuluje automatyczną maszynę Kawową.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Wzorzec typu

Wzorzec typu umożliwia obliczanie i konwersję zwięzłego typu. Gdy jest używany z instrukcją `switch`, aby wykonać dopasowanie do wzorca, sprawdza, czy wyrażenie można przekonwertować na określony typ, i, jeśli to możliwe, rzutuje go na zmienną tego typu. Jego składnia to:

```csharp
   case type varname
```

Where *Type* jest nazwą typu, do którego zostanie przekonwertowany wynik *wyrażenia* , a *nazwa_zmiennej* jest obiektem, do którego zostanie przekonwertowany wynik *wyrażenia* , jeśli dopasowanie się powiedzie. Typ "czas kompilacji" *wyrażenia* może być parametrem typu ogólnego, rozpoczynając od C# 7,1.

Wyrażenie `case` jest `true`, jeśli którykolwiek z następujących warunków jest spełniony:

- *wyrażenie* jest wystąpieniem tego samego typu co *Typ*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od *typu*. Innymi słowy, wynik *wyrażenia* może być rzutowany na wystąpienie *typu*.

- *wyrażenie* ma typ czasu kompilacji, który jest klasą bazową *typu*, a *wyrażenie* ma typ środowiska uruchomieniowego, który jest *typem* lub pochodzi od *typu*. *Typ czasu kompilacji* zmiennej to typ zmiennej, zgodnie z definicją w deklaracji typu. *Typ środowiska uruchomieniowego* zmiennej to typ wystąpienia, które jest przypisane do tej zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje interfejs *typu* .

Jeśli wyrażenie CASE ma wartość true, właściwość *nazwa_zmiennej* jest ostatecznie przypisana i ma zakres lokalny tylko w sekcji Switch.

Należy zauważyć, że `null` nie pasuje do typu. Aby dopasować `null`, należy użyć następującej etykiety `case`:

```csharp
case null:
```

Poniższy przykład używa wzorca typu, aby podać informacje dotyczące różnych rodzajów typów kolekcji.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Zamiast `object`można utworzyć metodę rodzajową przy użyciu typu kolekcji jako parametru typu, jak pokazano w poniższym kodzie:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Wersja ogólna różni się od pierwszej próbki na dwa sposoby. Najpierw nie można użyć przypadku `null`. Nie można użyć żadnego ze stałych przypadków, ponieważ kompilator nie może konwertować dowolnego dowolnego typu `T` na dowolny typ inny niż `object`. Co było `default` przypadku teraz testuje `object`o wartości innej niż null. Oznacza to, że `default` testy przypadku `null`.

Bez dopasowania do wzorca ten kod może być zapisany w następujący sposób. Użycie dopasowania wzorca typu daje bardziej zwarty, czytelny kod, eliminując konieczność sprawdzenia, czy wynik konwersji jest `null`, czy też do wykonywania powtarzających się rzutowania.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" /> instrukcji `case` i klauzuli `when`

Począwszy od C# 7,0, ponieważ instrukcje Case nie muszą się wzajemnie wykluczać, można dodać klauzulę `when`, aby określić dodatkowy warunek, który musi być spełniony dla instrukcji case, aby obliczyć wartość true. Klauzula `when` może być dowolnym wyrażeniem zwracającym wartość logiczną.

W poniższym przykładzie zdefiniowano klasę podstawową `Shape`, klasy `Rectangle`, która pochodzi od `Shape`i klasy `Square`, która pochodzi od `Rectangle`. Używa klauzuli `when`, aby upewnić się, że `ShowShapeInfo` traktuje `Rectangle` obiekt, do którego przypisano równe długości i szerokości jako `Square` nawet wtedy, gdy nie został skonkretyzowany jako obiekt `Square`. Metoda nie próbuje wyświetlić informacji o obiekcie `null` lub kształcie, którego obszar ma wartość zero.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Należy zauważyć, że klauzula `when` w przykładzie, która próbuje sprawdzić, czy obiekt `Shape` jest `null` nie jest wykonywany. Poprawna wzorzec typu do testowania dla `null` jest `case null:`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [instrukcję Switch](~/_csharplang/spec/statements.md#the-switch-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [if-else](if-else.md)
- [Dopasowanie do wzorca](../../pattern-matching.md)
