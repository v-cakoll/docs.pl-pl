---
title: Struktury — przewodnik języka C#
description: Dowiedz się więcej o typ struktury i jak je utworzyć
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 6fcd30907880be9159b3cc2e3ab10659ddec248b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979488"
---
# <a name="structs"></a>Struktury
A *struktury* jest typem wartości. Po utworzeniu struktury, zmienna, do którego jest przypisana struktura zawiera rzeczywiste dane struktury. Struktura jest przypisywana do nowej zmiennej, są kopiowane. Nowa zmienna i pierwotna zmienna zatem zawierają dwie oddzielne kopie tych samych danych. Zmiany wprowadzone w jednym egzemplarzu nie wpływają na drugi egzemplarz.

Zmienne typu wartości bezpośrednio zawierają swoje wartości, co oznacza, że pamięć jest alokowana wewnątrz niezależnie od kontekstu, ta zmienna została zgłoszona. Nie ma oddzielnej alokacji stosu lub wyrzucania elementów bezużytecznych dla zmiennych typu wartości.  
  
Istnieją dwie kategorie typów wartości: [struktury](./language-reference/keywords/struct.md) i [wyliczenia](./language-reference/keywords/enum.md).  
  
Wbudowane typy liczbowe są strukturami i mają właściwości i metody, do których masz dostęp:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ale zadeklarować i przypisać do nich wartości, tak jakby były one proste typami-aggregacji:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Typy wartości są *zapieczętowanego*, oznacza to, na przykład, że nie możesz wywodzić typu z <xref:System.Int32>, i nie możesz definiować dziedziczenia struktury od dowolnego użytkownika klasy lub struktury, ponieważ struktura może dziedziczyć tylko z <xref:System.ValueType> . Jednakże struktura może zaimplementować jeden lub więcej interfejsów. Można rzutować na typ interfejsu; typ struktury Powoduje to, że *pakowania* operację, aby opakować obiekt typu odwołania na stosie zarządzanym. Operacje na polach występują, gdy typ wartości są przekazywane do metody, która przyjmuje <xref:System.Object> jako parametr wejściowy. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](./programming-guide/types/boxing-and-unboxing.md ).  
  
Możesz użyć [struktury](./language-reference/keywords/struct.md) — słowo kluczowe, aby utworzyć własne typy niestandardowych wartości. Typowo, struct jest używany jako kontener dla mniejszego zestawu powiązanych zmiennych, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Aby uzyskać więcej informacji na temat typów wartości w programie .NET Framework, zobacz [Wspólny System typów](../standard/common-type-system.md).  
    
Struktury udostępniać większość tej samej składni jak klasy, chociaż struktur są bardziej ograniczone niż klasy:  
  
-   W deklaracji struktury, pola nie można zainicjować, chyba że są one zadeklarowane jako `const` lub `static`.  
  
-   Struktura nie można zadeklarować konstruktora bez parametrów (Konstruktor bez parametrów) lub finalizatora.  
  
-   Struktury są kopiowane w przydziale. Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii. Jest to ważne podczas pracy z kolekcjami typów wartości, takich jak Dictionary < string, myStruct >.  
  
-   Struktury są typami wartości i klasy są typami odwołań.  
  
-   W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.  
  
-   Struktury można zadeklarować konstruktorów, które mają parametry.  
  
-   Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy. Wszystkie struktury dziedziczyć bezpośrednio <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.  
  
-   Struktura może zaimplementować interfejsów.

## <a name="literal-values"></a>Wartości literałów  
W języku C# wartości literału otrzymują typ z kompilatora. Możesz określić jak literał liczbowy powinien wpisana przez dołączenie litery na końcu numeru. Na przykład aby określić, że wartość 4,56 powinny być traktowane jako zmiennoprzecinkowa, dołączyć "f" lub "F" po liczbie: `4.56f`. Jeśli żadna litera nie zostanie dołączony, kompilator wywnioskuje `double` typ dla literału. Aby uzyskać więcej informacji na temat tego, jakie typy można określić za pomocą literowych sufiksów, zobacz strony pomocy dla poszczególnych typów w [typów wartości](./language-reference/keywords/value-types.md).  
  
Ponieważ wpisywane są literały, a wszystkie typy ostatecznie pochodzą z <xref:System.Object>, można pisać i kompilować następujący kod:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

W ostatnich dwóch przykładach pokazano funkcje językowe, które wprowadzono w języku C# 7.0. Pierwszy pozwala na używanie znaku podkreślenia jako *separator cyfr* w literałach numerycznych. Można je umieścić wszędzie tam, gdzie ma się od cyfr w celu poprawienia czytelności. Mają one wpływu na wartość.

Drugi pokazuje *literały binarne*, które pozwalają na określenie wzorców bezpośrednio zamiast przy użyciu notacji szesnastkowej.

## <a name="nullable-types"></a>Typy dopuszczające wartości null  
Typy wartości zwykłych nie może mieć wartość [null](./language-reference/keywords/null.md). Można jednak utworzyć typy o wartości zerowalnej przez umieszczenie **?** po typie. Na przykład **int?** jest **int** typu, który może mieć również wartość [null](./language-reference/keywords/null.md). W CTS, typy null są wystąpieniami typu struktury ogólnej <xref:System.Nullable%601>. Typy dopuszczające wartości null są szczególnie przydatne podczas przekazywania danych do i z baz danych, w których wartości liczbowe mogą przyjąć wartości null. Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe (C# Programming Guide)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Zobacz także

- [Klasy](classes.md)
- [Typy podstawowe](basic-types.md)
