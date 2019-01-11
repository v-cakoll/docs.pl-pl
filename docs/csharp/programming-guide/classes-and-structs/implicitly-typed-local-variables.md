---
title: Niejawnie wpisane zmienne lokalne - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 9c6f7ae5d7a579abead2a62f8fdc7c63e5c53328
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222710"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Niejawnie wpisane zmienne lokalne (C# Programming Guide)

Zmienne lokalne, może być zadeklarowana bez jawnego typu. `var` — Słowo kluczowe nakazuje kompilatorowi wywnioskowania typu zmiennej z wyrażenie po prawej stronie instrukcji inicjowania. Wnioskowany typ może być wbudowany typ, typ anonimowy, typ zdefiniowany przez użytkownika lub typ zdefiniowany w bibliotece klas programu .NET Framework. Aby uzyskać więcej informacji o tym, jak zainicjować tablic z `var`, zobacz [niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md).

W poniższych przykładach pokazano różne sposoby, w których zmienne lokalne mogą być deklarowane przy użyciu `var`:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Należy pamiętać, że `var` — słowo kluczowe nie oznaczać "variant" i nie wskazuje, że zmienna jest luźno wpisane lub z późnym wiązaniem. Po prostu oznacza to, że kompilator określa i przypisuje najbardziej odpowiedniego typu.

`var` — Słowo kluczowe może być używana w kontekstach następujące:

- W zmiennych lokalnych (zmiennych zadeklarowanych w zakresie metoda) jak pokazano w poprzednim przykładzie.

- W [dla](../../language-reference/keywords/for.md) instrukcji inicjowania.

    ```csharp
    for(var x = 1; x < 10; x++)
    ```

- W [foreach](../../language-reference/keywords/foreach-in.md) instrukcji inicjowania.

    ```csharp
    foreach(var item in list){...}
    ```

- W [przy użyciu](../../language-reference/keywords/using-statement.md) instrukcji.

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Aby uzyskać więcej informacji, zobacz [jak: Użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>var i typy anonimowe

W wielu przypadkach użycia `var` jest opcjonalny, a to udogodnienie składni. Jednak gdy zmienna jest inicjowana za pomocą typu anonimowego należy zadeklarować zmienną jako `var` Jeśli chcesz uzyskać dostęp do właściwości obiektu w dowolnym momencie. Jest to typowy scenariusz w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Aby uzyskać więcej informacji, zobacz [typy anonimowe](anonymous-types.md).

Z punktu widzenia kodu źródłowego typ anonimowy nie ma nazwy. W związku z tym jeśli zmienna zapytania została zainicjowana przy użyciu `var`, a następnie jedynym sposobem, aby uzyskać dostęp do właściwości w zwracanej sekwencji obiektów jest użycie `var` jako typ zmiennej iteracji w `foreach` instrukcji.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Uwagi

Poniższe ograniczenia mają zastosowanie do deklaracji zmiennych wpisanych niejawnie:

- `var` można używać tylko w przypadku zmiennej lokalnej jest deklarowane i inicjowane w tej samej instrukcji; Nie można zainicjować zmiennej, na wartość null lub do grupy metoda lub funkcja anonimowa.

- `var` Nie można używać w polach w zakresie klasy.

- Zmienne zadeklarowane za pomocą `var` nie można używać w wyrażenia inicjowania. Innymi słowy, to wyrażenie jest legalna`: int i = (i = 20);` to wyrażenie powoduje błąd w czasie kompilacji: `var i = (i = 20);`

- Nie można zainicjować wiele zmiennych wpisanych niejawnie w tej samej instrukcji.

- Jeśli typ o nazwie `var` znajduje się w zakresie, a następnie `var` — słowo kluczowe zostanie rozwiązany w tej nazwy typu i nie będzie traktowane jako część niejawnie wpisane deklaracji zmiennej lokalnej.

Może się okazać, że `var` może być również przydatne w przypadku wyrażeń zapytania, w których jest trudny do określenia dokładnego skonstruowanego typu zmiennej zapytania. Może to być spowodowane grupowania i kolejność operacji.

`var` — Słowo kluczowe może być także przydatny podczas określonego typu zmiennej jest niewygodna do typu na klawiaturze, jest oczywiste lub nie zwiększa czytelność kodu. Jednym z przykładów gdzie `var` przydaje się w tym sposób jest zagnieżdżonych typów rodzajowych, takich jak używane z operacjami grupy. W następującym zapytaniu typ zmiennej zapytania jest `IEnumerable<IGrouping<string, Student>>`. Tak długo, jak Ty i inni, którzy muszą utrzymywać kod to zrozumieć, tam nie ma problemu przy użyciu niejawnego wpisywania dla wygody i skrócenia programu.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Jednak użycie `var` mieć co najmniej mogą sprawić, że kod jest trudniejszy do zrozumienia innym deweloperom. Z tego powodu, dokumentacja języka C# zazwyczaj używa `var` tylko jeśli jest to wymagane.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md)
- [Instrukcje: Użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Typy anonimowe](anonymous-types.md)
- [Inicjatory obiektów i kolekcji](object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [Wyrażenia zapytań LINQ](../linq-query-expressions/index.md)
- [LINQ (Language-Integrated Query)](../../linq/index.md)
- [for](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using, instrukcja](../../language-reference/keywords/using-statement.md)