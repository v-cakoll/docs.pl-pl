---
title: Niejawnie wpisane zmienne lokalne — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399827"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Niejawnie wpisane zmienne lokalne (Przewodnik programowania C#)

Zmienne lokalne można zadeklarować bez podawania typu jawnego. Słowo `var` kluczowe instruuje kompilator, aby wywnioskować typ zmiennej z wyrażenia po prawej stronie instrukcji inicjowania. Typ wywnioskowany może być typem wbudowanym, typem anonimowym, typem zdefiniowanym przez użytkownika lub typem zdefiniowanym w bibliotece klas .NET Framework. Aby uzyskać więcej informacji na temat `var`inicjowania tablic za pomocą , zobacz [Tablice niejawnie wpisane](../arrays/implicitly-typed-arrays.md).

Poniższe przykłady pokazują różne sposoby deklarowania zmiennych `var`lokalnych za pomocą:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Ważne jest, aby `var` zrozumieć, że słowo kluczowe nie oznacza "wariant" i nie wskazuje, że zmienna jest luźno wpisany lub późnym wiązaniem. Oznacza to po prostu, że kompilator określa i przypisuje najbardziej odpowiedni typ.

Słowo `var` kluczowe może być używane w następujących kontekstach:

- Zmienne lokalne (zmienne zadeklarowane w zakresie metody), jak pokazano w poprzednim przykładzie.

- W [instrukcji for](../../language-reference/keywords/for.md) inicjalizacji.

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- W instrukcji inicjalizacji [foreach.](../../language-reference/keywords/foreach-in.md)

    ```csharp
    foreach (var item in list) {...}
    ```

- W [using](../../language-reference/keywords/using-statement.md) instrukcji.

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Aby uzyskać więcej informacji, zobacz [Jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>typy var i anonimowe

W wielu przypadkach `var` użycie jest opcjonalne i jest tylko wygodą składni. Jednak gdy zmienna jest inicjowana z typem anonimowym należy zadeklarować zmienną tak, `var` jakby trzeba było uzyskać dostęp do właściwości obiektu w późniejszym punkcie. Jest to typowy scenariusz w wyrażeniach kwerend LINQ. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](anonymous-types.md).

Z punktu widzenia kodu źródłowego typ anonimowy nie ma nazwy. W związku z tym jeśli zmienna kwerendy została zainicjowana z `var`, a następnie jedynym `var` sposobem, aby uzyskać dostęp do `foreach` właściwości w zwróconej sekwencji obiektów jest użycie jako typ zmiennej iteracji w instrukcji.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Uwagi

Następujące ograniczenia mają zastosowanie do deklaracji zmiennych niejawnie wpisanych:

- `var`można używać tylko wtedy, gdy zmienna lokalna jest zadeklarowana i zainicjowana w tej samej instrukcji; zmiennej nie można zainicjować na wartość null, do grupy metod lub funkcji anonimowej.

- `var`nie można używać w polach w zakresie klasy.

- Zmienne zadeklarowane `var` przy użyciu za pomocą nie mogą być używane w wyrażeniu inicjowania. Innymi słowy to wyrażenie jest `int i = (i = 20);` legalne: ale to wyrażenie generuje błąd w czasie kompilacji:`var i = (i = 20);`

- Nie można zainicjować wielu zmiennych niejawnie wpisanych w tej samej instrukcji.

- Jeśli typ `var` o nazwie znajduje `var` się w zakresie, słowo kluczowe zostanie rozpoznane do tej nazwy typu i nie będą traktowane jako część niejawnie wpisane deklaracji zmiennej lokalnej.

Niejawne wpisywanie za pomocą słowa kluczowego `var` można zastosować tylko do zmiennych w zakresie metody lokalnej. Niejawne wpisywanie nie jest dostępne dla pól klas, ponieważ kompilator C# napotka logiczny paradoks podczas przetwarzania kodu: kompilator musi znać typ pola, ale nie może określić tego typu, dopóki wyrażenie przypisania nie zostanie przeanalizowane, a wyrażenie nie może zostać ocenione bez znajomości typu. Spójrzmy na poniższy kod:

```csharp
private var bookTitles;
```

`bookTitles`jest polem klasy, `var`biorąc pod uwagę typ . Ponieważ pole nie ma wyrażenia do oceny, kompilator nie `bookTitles` może wywnioskować, jaki typ ma być. Ponadto dodanie wyrażenia do pola (podobnie jak w przypadku zmiennej lokalnej) jest również niewystarczające:

```csharp
private var bookTitles = new List<string>();
```

Gdy kompilator napotka pola podczas kompilacji kodu, rejestruje typ każdego pola przed przetworzeniem wyrażeń skojarzonych z nim. Kompilator napotyka ten sam `bookTitles`paradoks próbuje przeanalizować: musi znać typ pola, `var`ale kompilator normalnie określić typ przez analizowanie wyrażenia, co nie jest możliwe bez wcześniejszego znajomości typu.

Może się `var` okazać, że może być również przydatne w przypadku wyrażeń kwerendy, w których trudno jest określić dokładny skonstruowany typ zmiennej kwerendy. Może to nastąpić w przypadku operacji grupowania i zamawiania.

Słowo `var` kluczowe może być również przydatne, gdy określony typ zmiennej jest żmudny, aby wpisać na klawiaturze lub jest oczywiste lub nie dodaje do czytelności kodu. Jednym z `var` przykładów, gdzie jest pomocne w ten sposób jest z zagnieżdżonych typów ogólnych, takich jak te używane z operacji grupy. W poniższej kwerendzie typem zmiennej kwerendy jest `IEnumerable<IGrouping<string, Student>>`. Tak długo, jak ty i inni, którzy muszą zachować kod zrozumieć to, nie ma problemu z użyciem niejawnego wpisywania dla wygody i zwięzłości.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Użycie `var` pomaga uprościć kod, ale jego użycie powinno być ograniczone do przypadków, gdy jest to wymagane lub gdy sprawia, że kod jest łatwiejszy do odczytania. Aby uzyskać więcej informacji `var` o tym, kiedy używać poprawnie, zobacz [niejawnie wpisane zmienne lokalne](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) sekcji w C# Coding Guidelines artykułu.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Niejawnie wpisane tablice](../arrays/implicitly-typed-arrays.md)
- [Jak używać niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Typy anonimowe](anonymous-types.md)
- [Inicjatory obiektów i kolekcji](object-and-collection-initializers.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ w C#](../../linq/index.md)
- [LINQ (zapytanie zintegrowane z językiem)](../../linq/index.md)
- [for](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [za pomocą instrukcji](../../language-reference/keywords/using-statement.md)
