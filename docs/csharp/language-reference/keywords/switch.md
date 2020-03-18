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
ms.openlocfilehash: e5580e81b9175cd95491fdba724bacbffa692a5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345395"
---
# <a name="switch-c-reference"></a>przełącznik (odwołanie do języka C#)

`switch`jest instrukcją wyboru, która wybiera *pojedynczą sekcję przełącznika* do wykonania z listy kandydatów na podstawie dopasowania wzorca do *wyrażenia dopasowania*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Instrukcja `switch` jest często używana jako alternatywa dla konstrukcji [if-else,](if-else.md) jeśli pojedyncze wyrażenie jest testowane na trzy lub więcej warunków. Na przykład następująca `switch` instrukcja określa, `Color` czy zmienna typu ma jedną z trzech wartości:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Jest to odpowiednik następującego przykładu, `if` - `else` który używa konstrukcji.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Wyrażenie dopasowania

Wyrażenie dopasowania zapewnia wartość, aby dopasować `case` do wzorców w etykietach. Jego składnia jest:

```csharp
   switch (expr)
```

W języku C# 6 i starszym wyrażenie dopasowania musi być wyrażeniem zwracającym wartość następujących typów:

- [char](../builtin-types/char.md).
- [ciąg .](../builtin-types/reference-types.md)
- [bool](../builtin-types/bool.md).
- wartości [integralnej,](../builtin-types/integral-numeric-types.md) takiej `int` jak `long`wartość lub .
- wartości [wyliczenia.](../builtin-types/enum.md)

Począwszy od Języka C# 7.0 wyrażenie dopasowania może być dowolne wyrażenie inne niż null.

## <a name="the-switch-section"></a>Sekcja przełącznika

Instrukcja `switch` zawiera jedną lub więcej sekcji przełącznika. Każda sekcja przełącznika zawiera jedną lub więcej *etykiet sprawy* (case lub etykietę domyślną), po której następuje jedna lub więcej instrukcji. Instrukcja `switch` może zawierać co najwyżej jedną domyślną etykietę umieszczoną w dowolnej sekcji przełącznika. W poniższym przykładzie `switch` przedstawiono prostą instrukcję, która ma trzy sekcje przełącznika, z których każda zawiera dwie instrukcje. Druga sekcja przełącznika `case 2:` `case 3:` zawiera etykiety i etykiety.

Instrukcja `switch` może zawierać dowolną liczbę sekcji przełącznika, a każda sekcja może mieć jedną lub więcej etykiet sprawy, jak pokazano w poniższym przykładzie. Jednak nie dwie etykiety przypadku może zawierać to samo wyrażenie.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Wykonuje się tylko jedną sekcję przełącznika w instrukcji switch. C# nie zezwala na wykonywanie kontynuować z jednej sekcji przełącznika do następnego. Z tego powodu następujący kod generuje błąd kompilatora, CS0163: "Kontrola\<nie może przechodzić z jednej etykiety przypadku (etykieta przypadku>) do innego."

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

Wymóg ten jest zwykle spełniony przez jawne zamknięcie sekcji przełącznika za pomocą [instrukcji break,](break.md) [goto](goto.md)lub [return.](return.md) Jednak poniższy kod jest również prawidłowy, ponieważ zapewnia, że kontrola `default` programu nie może przechodzić do sekcji przełączania.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Wykonanie listy instrukcji w sekcji przełącznika z etykietą przypadku, która pasuje do wyrażenia dopasowania, rozpoczyna się od pierwszej `break`instrukcji `goto case` `goto label`i `return`przechodzi `throw`przez listę instrukcji, zazwyczaj do momentu osiągnięcia instrukcji skoku, takiej jak , , , , lub , . W tym momencie kontrola jest `switch` przekazywana poza instrukcję lub do innej etykiety sprawy. Instrukcja, `goto` jeśli jest używana, musi przenieść kontrolę do stałej etykiety. To ograniczenie jest konieczne, ponieważ próba przeniesienia kontroli do etykiety niestałej może mieć niepożądane skutki uboczne, takie przeniesienie kontroli do niezamierzonej lokalizacji w kodzie lub tworzenie nieskończonej pętli.

## <a name="case-labels"></a>Etykiety obudowy

Każda etykieta przypadku określa wzorzec do `caseSwitch` porównania z wyrażeniem dopasowania (zmienna w poprzednich przykładach). Jeśli są one zgodne, formant jest przenoszony do sekcji przełącznika, który zawiera **pierwszą** etykietę pasującego przypadku. Jeśli żaden wzorzec etykiety przypadku nie pasuje do `default` wyrażenia dopasowania, formant jest przenoszony do sekcji z etykietą sprawy, jeśli istnieje. Jeśli nie ma `default` przypadku, żadne instrukcje w sekcji przełącznika są wykonywane, a kontrola jest przekazywana poza instrukcję. `switch`

Aby uzyskać `switch` informacje na temat dopasowania instrukcji i wzorca, zobacz [pattern dopasowania do `switch` instrukcji](#pattern) sekcji.

Ponieważ C# 6 obsługuje tylko wzorzec stały i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości i tylko jeden wzorzec może odpowiadać wyrażeniu dopasowania. W rezultacie kolejność, `case` w jakiej pojawiają się instrukcje, jest nieistotna.

W języku C# 7.0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczające się wartości i wiele wzorców można dopasować wyrażenie dopasowania. Ponieważ wykonywane są tylko instrukcje w pierwszej sekcji przełącznika, `case` która zawiera pasujący wzorzec, kolejność, w jakiej pojawiają się instrukcje, jest teraz ważna. Jeśli C# wykryje sekcję przełączania, której instrukcje case lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120, "Sprawa przełącznika została już obsłużena przez poprzedni przypadek."

W poniższym przykładzie `switch` przedstawiono instrukcję, która używa różnych wzorców nie wykluczasię wzajemnie. Jeśli `case 0:` przesuniesz sekcję przełącznika tak, aby nie `switch` była już pierwszą sekcją w instrukcji, C# generuje błąd kompilatora, ponieważ liczba całkowita, `case int val` której wartość wynosi zero, jest podzbiorem wszystkich liczb całkowitych, który jest wzorcem zdefiniowanym przez instrukcję.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Ten problem można rozwiązać i wyeliminować ostrzeżenie kompilatora na jeden z dwóch sposobów:

- Zmieniając kolejność sekcji przełącznika.

- Za pomocą [when klauzuli](#when) w etykiecie. `case`

## <a name="the-default-case"></a>Sprawa `default`

Przypadek `default` określa sekcję switch do wykonania, jeśli wyrażenie dopasowania `case` nie pasuje do żadnej innej etykiety. Jeśli `default` sprawa nie jest obecna, a wyrażenie dopasowania `case` nie pasuje do `switch` żadnej innej etykiety, przepływ programu przechodzi przez instrukcję.

Sprawa `default` może pojawić się w `switch` dowolnej kolejności w oświadczeniu. Niezależnie od jego kolejności w kodzie źródłowym, zawsze jest `case` oceniana jako ostatnia, po ocenie wszystkich etykiet.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" />Dopasowanie wzorca `switch` do instrukcji

Każda `case` instrukcja definiuje wzorzec, który, jeśli pasuje do wyrażenia dopasowania, powoduje, że jego sekcja przełącznika zawierające do wykonania. Wszystkie wersje języka C# obsługują wzorzec stały. Pozostałe wzorce są obsługiwane począwszy od języka C# 7.0.

### <a name="constant-pattern"></a>Stały wzór

Wzorzec stały sprawdza, czy wyrażenie dopasowania jest równe określonej stałej. Jego składnia jest:

```csharp
   case constant:
```

gdzie *stała* jest wartością do przetestowania. *stała* może być dowolne z następujących wyrażeń stałych:

- [Bool](../builtin-types/bool.md) dosłowny: albo `true` lub `false`.
- Każda [stała integralna,](../builtin-types/integral-numeric-types.md) `int`taka `long`jak `byte`, a , lub .
- Nazwa zadeklarowanej `const` zmiennej.
- Stała wyliczenia.
- [Char](../builtin-types/char.md) dosłowne.
- Literał [ciągu.](../builtin-types/reference-types.md)

Wyrażenie stałe jest oceniane w następujący sposób:

- Jeśli *expr* i *stała* są typami integralnymi, operator `true` równości Języka C# określa, czy wyrażenie zwraca (czyli czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [Object.Equals(expr, stała)](xref:System.Object.Equals(System.Object,System.Object)) metoda.

W poniższym przykładzie użyto stałego wzorca, aby określić, czy dana data jest weekendem, pierwszym dniem tygodnia roboczego, ostatnim dniem tygodnia roboczego lub środkiem tygodnia roboczego. Oblicza <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwość bieżącego dnia względem członków wyliczenia. <xref:System.DayOfWeek>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

W poniższym przykładzie użyto stałego wzorca do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje automatyczny ekspres do kawy.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Wzorzec tekstu

Wzorzec typu umożliwia zwięzłe oceny typu i konwersji. W przypadku `switch` użycia z instrukcją do wykonywania dopasowania wzorca, sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może być, rzutuje go do zmiennej tego typu. Jego składnia jest:

```csharp
   case type varname
```

gdzie *typ* jest nazwą typu, na który wynik *expr* ma zostać przekonwertowany, a *varname* jest obiektem, na który jest konwertowany wynik *expr,* jeśli dopasowanie zakończy się pomyślnie. Typ czasu kompilacji *expr* może być parametrtypu ogólnego, począwszy od C# 7.1.

Wyrażenie `case` jest, `true` jeśli którakolwiek z następujących wartości jest true:

- *expr* jest wystąpieniem tego samego typu co *typ*.

- *expr* jest wystąpieniem typu, który pochodzi od *typu*. Innymi słowy wynik *expr* może być rzutnie na wystąpienie *typu*.

- *expr* ma typ kompilacji w czasie, który jest klasą podstawową *typu*, a *expr* ma typ czasu wykonywania, który jest *typem* lub pochodzi od *typu*. *Typ czasu kompilacji* zmiennej jest typem zmiennej zdefiniowanym w deklaracji typu. *Typ czasu wykonywania* zmiennej jest typem wystąpienia przypisanego do tej zmiennej.

- *expr* jest wystąpieniem typu, który implementuje interfejs *typu.*

Jeśli wyrażenie sprawy jest prawdziwe, *varname* jest zdecydowanie przypisany i ma zakres lokalny tylko w sekcji przełącznika.

Pamiętaj, `null` że nie pasuje do typu. Aby dopasować `null`, należy `case` użyć następującej etykiety:

```csharp
case null:
```

W poniższym przykładzie użyto wzorca typu, aby zapewnić informacje o różnych typach typów kolekcji.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Zamiast `object`, można zrobić metodę rodzajową, przy użyciu typu kolekcji jako parametr typu, jak pokazano w następującym kodzie:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Wersja ogólna różni się od pierwszej próbki na dwa sposoby. Po pierwsze, nie można `null` użyć sprawy. Nie można użyć żadnej stałej sprawy, ponieważ kompilator `T` nie może `object`przekonwertować dowolnego typu na dowolny typ inny niż . Co było `default` w przypadku teraz testy `object`dla non-null . Oznacza to, że `default` `null`testy przypadku tylko dla .

Bez dopasowywania wzorców ten kod może być napisany w następujący sposób. Użycie dopasowania wzorca typu tworzy bardziej kompaktowy, czytelny kod, eliminując konieczność `null` testowania, czy wynik konwersji jest lub do wykonywania wielokrotnych rzutowania.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" />Oświadczenie `case` i `when` klauzula

Począwszy od języka C# 7.0, ponieważ instrukcje case nie `when` muszą się wzajemnie wykluczać, można dodać klauzulę, aby określić dodatkowy warunek, który musi być spełniony dla instrukcji case, aby ocenić wartość true. Klauzula `when` może być dowolne wyrażenie, które zwraca wartość logiczną.

Poniższy przykład definiuje klasę `Shape` podstawową, `Rectangle` klasę, `Shape`która pochodzi `Square` z , `Rectangle`i klasy, która pochodzi od . Używa `when` klauzuli, aby `ShowShapeInfo` upewnić się, że traktuje `Rectangle` obiekt, który został przypisany równe długości i szerokości jako `Square` `Square` nawet jeśli nie został utworzyony jako obiekt. Metoda nie próbuje wyświetlić informacji o obiekcie, `null` który jest lub kształt, którego obszar wynosi zero.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Należy zauważyć, że klauzula `when` w przykładzie, który próbuje sprawdzić, `Shape` czy obiekt nie jest `null` wykonywany. Prawidłowy wzorzec `null` typu `case null:`do testowania dla a jest .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Switch instrukcji](~/_csharplang/spec/statements.md#the-switch-statement) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [if-else](if-else.md)
- [Dopasowywanie wzorców](../../pattern-matching.md)
