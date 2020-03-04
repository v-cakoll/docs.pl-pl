---
title: Niejawnie wpisane zmienne lokalne C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241003"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Niejawnie wpisane zmienne lokalneC# (Przewodnik programowania)

Zmienne lokalne można deklarować bez udzielania jawnego typu. Słowo kluczowe `var` instruuje kompilator do wywnioskowania typu zmiennej z wyrażenia po prawej stronie instrukcji inicjującej. Typ wnioskowany może być typem wbudowanym, typem anonimowym, typem zdefiniowanym przez użytkownika lub typem zdefiniowanym w bibliotece klas .NET Framework. Aby uzyskać więcej informacji na temat inicjowania tablic z `var`, zobacz [niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md).

W poniższych przykładach pokazano różne sposoby deklarowania zmiennych lokalnych przy użyciu `var`:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Ważne jest, aby zrozumieć, że słowo kluczowe `var` nie ma znaczenia "Variant" i nie wskazuje, że zmienna jest luźno wpisana lub późna. Oznacza to, że kompilator określa i przypisuje najbardziej odpowiedni typ.

Słowo kluczowe `var` może być używane w następujących kontekstach:

- W przypadku zmiennych lokalnych (zmienne zadeklarowane w zakresie metody), jak pokazano w poprzednim przykładzie.

- W instrukcji [for](../../language-reference/keywords/for.md) inicjującej.

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- W instrukcji inicjującej [foreach](../../language-reference/keywords/foreach-in.md) .

    ```csharp
    foreach (var item in list) {...}
    ```

- W instrukcji [using](../../language-reference/keywords/using-statement.md) .

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Aby uzyskać więcej informacji, zobacz [jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>typy var i Anonymous

W wielu przypadkach użycie `var` jest opcjonalne i jest tylko wygodą składni. Jeśli jednak zmienna jest inicjowana z typem anonimowym, należy zadeklarować zmienną jako `var`, jeśli chcesz uzyskać dostęp do właściwości obiektu w późniejszym momencie. Jest to typowy scenariusz w wyrażeniach zapytań LINQ. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](anonymous-types.md).

Z perspektywy kodu źródłowego typ anonimowy nie ma nazwy. W związku z tym, jeśli zmienna zapytania została zainicjowana przy użyciu `var`, jedynym sposobem uzyskania dostępu do właściwości w zwracanej sekwencji obiektów jest użycie `var` jako typu zmiennej iteracji w instrukcji `foreach`.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Uwagi

Następujące ograniczenia dotyczą deklaracji zmiennej o typie określonym niejawnie:

- `var` można używać tylko wtedy, gdy zmienna lokalna jest zadeklarowana i zainicjowana w tej samej instrukcji; nie można zainicjować zmiennej do wartości null lub do grupy metod lub funkcji anonimowej.

- nie można używać `var` dla pól w zakresie klasy.

- Zmienne zadeklarowane za pomocą `var` nie mogą być używane w wyrażeniu inicjalizacji. Innymi słowy, to wyrażenie jest dozwolone: `int i = (i = 20);` ale to wyrażenie powoduje błąd czasu kompilacji: `var i = (i = 20);`

- W tej samej instrukcji nie można zainicjować wielu niejawnie wpisanych zmiennych.

- Jeśli typ o nazwie `var` znajduje się w zakresie, wówczas słowo kluczowe `var` zostanie rozpoznane jako nazwa tego typu i nie będzie traktowane jako część niejawnie wpisanej deklaracji zmiennej lokalnej.

Niejawne wpisywanie za pomocą słowa kluczowego `var` może być stosowane tylko do zmiennych w zakresie metody lokalnej. Niejawne wpisywanie nie jest dostępne w przypadku C# pól klas, ponieważ kompilator napotyka logiczną Paradox w miarę przetwarzania kodu: kompilator musi znać typ pola, ale nie może ustalić typu do czasu przeanalizowania wyrażenia przypisania, a wyrażenia nie można ocenić bez znajomości typu. Rozważmy następujący kod:

```csharp
private var bookTitles;
```

`bookTitles` to pole klasy, którego typ to `var`. Ponieważ pole nie ma wyrażenia do obliczenia, nie jest możliwe, aby kompilator mógł wnioskować, jakiego typu `bookTitles` ma być. Ponadto dodanie wyrażenia do pola (na przykład dla zmiennej lokalnej) jest również niewystarczające:

```csharp
private var bookTitles = new List<string>();
```

Gdy kompilator napotyka pola podczas kompilacji kodu, rejestruje każdy typ pola przed przetworzeniem skojarzonych z nim wyrażeń. Kompilator napotyka ten sam program Paradox, próbując przeanalizować `bookTitles`: musi znać typ pola, ale kompilator zwykle określa typ `var`, analizując wyrażenie, które nie jest możliwe bez uprzedniego poznania typu.

Może się okazać, że `var` może być również przydatne w przypadku wyrażeń zapytania, w których dokładny, skonstruowany typ zmiennej zapytania jest trudny do określenia. Może się to zdarzyć w przypadku operacji grupowania i porządkowania.

Słowo kluczowe `var` może być również przydatne, gdy określony typ zmiennej jest żmudnym do wpisywania na klawiaturze lub jest oczywiste lub nie dodaje do czytelności kodu. Przykład, w którym `var` jest pomocne w ten sposób, to z zagnieżdżonych typów ogólnych, takich jak te używane w przypadku operacji grupowych. W poniższym zapytaniu typ zmiennej zapytania jest `IEnumerable<IGrouping<string, Student>>`. Tak długo, jak ty i inne osoby, które muszą zachować ten kod, nie występują problemy z użyciem niejawnego wpisywania dla wygody i zwięzłości.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Użycie `var` pomaga uprościć kod, ale jego użycie powinno być ograniczone do przypadków, w których jest wymagane, lub gdy ułatwia odczytywanie kodu. Aby uzyskać więcej informacji o tym, kiedy należy prawidłowo używać `var`, zobacz sekcję " [niejawnie wpisane zmienne lokalne](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) " w artykule z instrukcjami dotyczącymi C# kodowania.

## <a name="see-also"></a>Zobacz też

- [C#Odwoła](../../language-reference/index.md)
- [Niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md)
- [Jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Typy anonimowe](anonymous-types.md)
- [Inicjatory obiektów i kolekcji](object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ w C#](../../linq/index.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/index.md)
- [for](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using, instrukcja](../../language-reference/keywords/using-statement.md)
