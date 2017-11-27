---
title: "Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Niejawnie wpisane zmienne lokalne (Przewodnik programowania w języku C#)
Zmienne lokalne mogą być deklarowane bez jawnego typu. `var` — Słowo kluczowe nakazuje kompilatorowi do wywnioskowania typu zmienną z wyrażenie po prawej stronie instrukcji inicjowania. Wnioskowany typ może być typem wbudowanym, typu anonimowego, typu zdefiniowanego przez użytkownika lub typ zdefiniowany w bibliotece klas programu .NET Framework. Aby uzyskać więcej informacji dotyczących sposobu inicjowania tablic o `var`, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 W poniższych przykładach pokazano różne sposoby, w których zmienne lokalne mogą być deklarowane z `var`:  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Należy pamiętać, że `var` — słowo kluczowe nie oznacza "variant" i nie wskazuje, że zmienna jest luźno wpisana lub późnym wiązaniem. Po prostu oznacza, że kompilator określa i przypisuje najbardziej odpowiedniego typu.  
  
 `var` — Słowo kluczowe może być używany w następujących sytuacjach:  
  
-   Zmienne lokalne (zmiennych zadeklarowanych w zakresie metody) jak pokazano w poprzednim przykładzie.  
  
-   W [dla](../../../csharp/language-reference/keywords/for.md) instrukcji inicjowania.  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   W [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji inicjowania.  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   W [przy użyciu](../../../csharp/language-reference/keywords/using-statement.md) instrukcji.  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu zapytania](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>var i typy anonimowe  
 W wielu przypadkach użycia `var` jest opcjonalna i składni udogodnienie. Jednak gdy zmienna jest zainicjowana z typu anonimowego należy zadeklarować zmienną jako `var` Jeśli musisz mieć dostęp do właściwości obiektu w późniejszym czasie. Jest to częsty przypadek w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Z perspektywy kod źródłowy typ anonimowy nie ma nazwy. W związku z tym Jeśli zmienną zapytania został zainicjowany z `var`, a następnie jedynym sposobem, aby uzyskać dostęp do właściwości w sekwencji zwróconych obiektów jest użycie `var` jako typ zmiennej iteracji w `foreach` instrukcji.  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 W typie określonym niejawnie deklaracjach zmiennych, obowiązują następujące ograniczenia:  
  
-   `var`można użyć tylko, gdy zmienna lokalna jest zadeklarowany i zainicjowane w tej samej instrukcji; Nie można zainicjować zmiennej, null, lub do grupy metod lub funkcji anonimowej.  
  
-   `var`Nie można używać pól w zakresie klasy.  
  
-   Zmienne zadeklarowane za pomocą `var` nie można użyć w wyrażeniu inicjowania. Innymi słowy, to wyrażenie jest dozwolony`: int i = (i = 20);` to wyrażenie powoduje błąd kompilacji:`var i = (i = 20);`  
  
-   W tej samej instrukcji nie można zainicjować wielu zmienne o typie określonym niejawnie.  
  
-   Jeśli typ o nazwie `var` znajduje się w zakresie, a następnie `var` — słowo kluczowe rozwiąże tej nazwy typu i nie będzie traktowane jako część niejawnie wpisane deklaracji zmiennej lokalnej.  
  
 Może się okazać, że `var` mogą być przydatne w przypadku wyrażenia zapytań, w których jest trudne do ustalenia dokładnego skonstruowanego typu zmienną zapytania. Taka sytuacja może wystąpić z grupowanie i kolejność operacji.  
  
 `var` — Słowo kluczowe może również być przydatne określonego typu zmienną jest niewygodne wpisz na klawiaturze lub jest jasne lub nie dodaje do czytelność kodu. Przykładem gdzie `var` jest przydatne w tym sposób się zagnieżdżonych typów ogólnych, takich jak używana z operacjami grupy. W następującym zapytaniu jest typu zmienną zapytania `IEnumerable<IGrouping<string, Student>>`. Tak długo, jak to zrozumieć użytkowników muszą zachować swój kod, brak problemy z przy użyciu niejawnego wpisując dla wygody i skrócenia.  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Jednak użycie `var` mieć co najmniej może utrudnić kodu zrozumiały dla innych deweloperów. Z tego powodu używa ogólnie dokumentacji C# `var` tylko gdy jest wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [Porady: użycie niejawnie wpisanych zmiennych lokalnych i tablic w wyrażeniu kwerendy](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [dla](../../../csharp/language-reference/keywords/for.md)  
 [Instrukcja foreach w](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Using — instrukcja](../../../csharp/language-reference/keywords/using-statement.md)
