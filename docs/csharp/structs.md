---
title: Struktury — przewodnik C#
description: Dowiedz się więcej o typie struktury i sposób ich tworzenia
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 9fe4e0278ecf46f762a93aa489030c0a9e5563b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="structs"></a>Struktury
A *struktury* jest typem wartości. Podczas tworzenia struktury zmiennej, do której przypisano struktury zawiera struktury danych rzeczywistych. Struktura jest przypisany do nowej zmiennej, są kopiowane. Nową zmienną i pierwotnej zmiennej w związku z tym zawierają dwa osobne kopie tych samych danych. Zmiany wprowadzone w jednej kopii nie wpływają na innej kopii.

Wartość typu zmienne bezpośrednio zawierać ich wartości, co oznacza, że pamięć jest przydzielona wbudowany w dowolnym kontekście zmienna została zadeklarowana. Nie jest alokacja sterty oddzielne ani odzyskiwanie kolekcji narzut na typ wartości zmiennych.  
  
Istnieją dwie kategorie typów wartości: [struktury](./language-reference/keywords/struct.md) i [wyliczenia](./language-reference/keywords/enum.md).  
  
Mają właściwości i metody, do których masz dostęp, i struktury są wbudowane typy liczbowe:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ale deklaruje i przypisać do nich wartości, tak jakby były to proste typy niezagregowanym:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Typy wartości są *zapieczętowanego*, co oznacza, na przykład, że nie może pochodzić od typu <xref:System.Int32>, i nie może definiować strukturę odziedziczone zdefiniowane przez użytkownika klasy lub struktury, ponieważ struktury może dziedziczyć tylko z <xref:System.ValueType> . Jednak struktury można zaimplementować jeden lub więcej interfejsów. Można rzutować typu struct na typ interfejsu; Powoduje to *boxing* operacji opakowywać struktury wewnątrz obiektu typu odwołania na stercie zarządzanej. OPAKOWYWANIE operacje są wykonywane, gdy typ wartości jest przekazywane do metody pobierającej <xref:System.Object> jako parametr wejściowy. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](./programming-guide/types/boxing-and-unboxing.md ).  
  
Możesz użyć [struktury](./language-reference/keywords/struct.md) — słowo kluczowe do tworzenia własnych typów wartości niestandardowych. Zazwyczaj struktury służy jako kontener dla małych zestawu powiązanych zmiennych, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Aby uzyskać więcej informacji na temat typów wartości w programie .NET Framework, zobacz [Wspólny System typów](../standard/common-type-system.md).  
    
Struktury udziału większość takiej samej składni jak klasy, struktury są bardziej ograniczone niż klasy:  
  
-   W deklaracji struktury pól nie można zainicjować, chyba że zostały zgłoszone jako `const` lub `static`.  
  
-   Struktury nie można zadeklarować konstruktora domyślnego (Konstruktor bez parametrów) lub finalizatora.  
  
-   Struktury są kopiowane na przypisanie. Gdy struktury jest przypisany do nowej zmiennej, wszystkie dane zostaną skopiowane, a wszelkie zmiany nowej kopii nie zmienia dane oryginał. Jest to ważne podczas pracy z kolekcjami typów wartości, takich jak słownik < string, myStruct >.  
  
-   Struktury są typy wartości i typy referencyjne występują następujące klasy.  
  
-   W przeciwieństwie do klasy, struktury można wdrożyć bez użycia `new` operatora.  
  
-   Struktury mogą zadeklarować konstruktorów, które mają parametry.  
  
-   Struktury nie może dziedziczyć z innego struktury lub klasy, a nie może być podstawą klasy. Strukturami dziedziczyć bezpośrednio po <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.  
  
-   Struktury mogą implementować interfejsów.

## <a name="literal-values"></a>Wartości literałów  
W języku C# wartości literałów otrzymywane z kompilatora. Można określić, jak literał liczbowy należy wpisać przez dołączenie list na końcu numeru. Na przykład, aby określić, że wartość 4.56 powinny być traktowane jako wartości zmiennoprzecinkowej, Dołącz "f" lub "F" po wartości: `4.56f`. Jeśli litera nie jest dołączana, kompilator wywnioskuje `double` typ literału. Aby uzyskać więcej informacji o tym, które można określić typy z sufiksy litera, zobacz strony podręcznika dla poszczególnych typów w [typów wartości](./language-reference/keywords/value-types.md).  
  
Ponieważ wpisywania literały, a wszystkie typy ostatecznie pochodzi z <xref:System.Object>, możesz zapisać i skompilować kod, takie jak następujące:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Ostatnie dwa przykłady pokazują funkcje językowe wprowadzono w języku C# w wersji 7.0. Pierwszy umożliwia przy użyciu znaku podkreślenia jako *separator cyfr* w literałach numerycznych. Możesz też zaznaczyć je wszędzie tam, gdzie ma cyfr w celu zwiększenia czytelności. Ich nie mają wpływu na wartość.

Drugi przedstawia *binarne literały*, pozwalają określić wzorce bit bezpośrednio, zamiast szesnastkowym.

## <a name="nullable-types"></a>Typy dopuszczające wartości null  
Typy wartości zwykłej nie może mieć wartości [null](./language-reference/keywords/null.md). Można jednak utworzyć typy dopuszczające wartości zerowe wartości przez umieszczenie **?** po typie. Na przykład **int?** jest **int** typu, który ma także wartość [null](./language-reference/keywords/null.md). W CTS, typy dopuszczające wartości null są wystąpienia typu ogólnego struktury <xref:System.Nullable%601>. Typy dopuszczające wartości null są szczególnie przydatne, gdy są przekazywanie danych do i z baz danych, w których wartości liczbowych może mieć wartości null. Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe (C# przewodnik programowania w języku)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Zobacz także
[Klasy](classes.md)

[Typy podstawowe](basic-types.md)
