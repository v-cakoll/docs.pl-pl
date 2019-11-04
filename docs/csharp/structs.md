---
title: Struktury — C# Przewodnik
description: Dowiedz się więcej na temat typu struktury i sposobu ich tworzenia
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 10971dc1a0b2c9d64ac8766734b3f6f630aa3ccf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423117"
---
# <a name="structs"></a>Struktury

*Struktura* jest typem wartości. Po utworzeniu struktury zmienna, do której jest przypisana struktura, zawiera rzeczywiste dane struktury. Gdy struktura jest przypisana do nowej zmiennej, zostanie ona skopiowana. Nowa zmienna i oryginalna zmienna w związku z tym zawierają dwie oddzielne kopie tych samych danych. Zmiany wprowadzone w jednej kopii nie mają wpływu na inną kopię.

Zmienne typu wartości bezpośrednio zawierają swoje wartości, co oznacza, że pamięć jest alokowana w dowolnym kontekście, w którym jest zadeklarowana zmienna. Nie ma oddzielnego przydziału sterty lub wyrzucania elementów bezużytecznych dla zmiennych typu wartości.  
  
Istnieją dwie kategorie typów wartości: [struct](./language-reference/keywords/struct.md) i [enum](./language-reference/keywords/enum.md).  
  
Wbudowane typy liczbowe to struktury i mają właściwości i metody, do których można uzyskać dostęp:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ale deklaruję i przypisujesz wartości do nich, tak jakby były to proste typy nieagregujące:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Typy wartości są *zapieczętowane*, co oznacza, że na przykład nie można utworzyć typu z <xref:System.Int32>i nie można zdefiniować struktury dziedziczonej z żadnej klasy lub struktury zdefiniowanej przez użytkownika, ponieważ struktura może dziedziczyć tylko po <xref:System.ValueType>. Jednak struktura może zaimplementować jeden lub więcej interfejsów. Typ struktury można rzutować na typ interfejsu; powoduje *to, że operacja opakowywania* otacza strukturę wewnątrz obiektu typu odwołania na zarządzanym stosie. Operacje pakowania są wykonywane, gdy przekazujesz typ wartości do metody, która przyjmuje <xref:System.Object> jako parametr wejściowy. Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](./programming-guide/types/boxing-and-unboxing.md ).  
  
Za pomocą słowa kluczowego [struct](./language-reference/keywords/struct.md) można tworzyć własne niestandardowe typy wartości. Zazwyczaj struktura jest używana jako kontener dla małego zestawu powiązanych zmiennych, jak pokazano w następującym przykładzie:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Aby uzyskać więcej informacji na temat typów wartości w .NET Framework, zobacz [Common Type System](../standard/common-type-system.md).  
    
Struktury współużytkują większość tej samej składni co klasy, chociaż struktury są bardziej ograniczone niż klasy:  
  
- W deklaracji struktury nie można inicjować pól, chyba że są one zadeklarowane jako `const` lub `static`.  
  
- Struktura nie może deklarować bezparametrowego konstruktora (Konstruktor bez parametrów) lub finalizatora.  
  
- Struktury są kopiowane podczas przypisywania. Gdy struktura jest przypisana do nowej zmiennej, wszystkie dane są kopiowane i wszelkie modyfikacje nowej kopii nie zmieniają danych dla oryginalnej kopii. Jest to ważne, aby pamiętać, że podczas pracy z kolekcjami typów wartości, takimi jak słownik < ciągu, moja Struktura >.  
  
- Struktury są typami wartości, a klasy są typami referencyjnymi.  
  
- W przeciwieństwie do klas, struktury mogą być tworzone bez użycia operatora `new`.  
  
- Struktury mogą deklarować konstruktory z parametrami.  
  
- Struktura nie może dziedziczyć z innej struktury lub klasy i nie może być podstawą klasy. Wszystkie struktury dziedziczą bezpośrednio z <xref:System.ValueType>, które dziedziczą z <xref:System.Object>.  
  
- Struktura może implementować interfejsy.

## <a name="literal-values"></a>Wartości literału

W C#programie wartości literałów otrzymują typ z kompilatora. Możesz określić sposób wpisywania literału liczbowego, dołączając literę do końca liczby. Na przykład, aby określić, że wartość 4,56 powinna być traktowana jako zmiennoprzecinkowa, należy dołączyć "f" lub "F" po liczbie: `4.56f`. Jeśli nie zostanie dołączona żadna litera, kompilator wykryje typ `double` dla literału. Aby uzyskać więcej informacji na temat typów, które można określić za pomocą sufiksów liter, zobacz strony referencyjne dla poszczególnych typów w [typach wartości](./language-reference/keywords/value-types.md).  
  
Ponieważ wpisywane są literały, a wszystkie typy są ostatecznie z <xref:System.Object>, można napisać i skompilować kod, taki jak następujące:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

W ostatnich dwóch przykładach przedstawiono funkcje języka wprowadzone C# w 7,0. Pierwszy umożliwia użycie znaku podkreślenia jako *separatora cyfr* wewnątrz literałów liczbowych. Możesz umieścić je wszędzie tam, gdzie chcesz, aby zwiększyć czytelność. Nie mają one wpływu na wartość.

Druga ilustruje *literały binarne*, które umożliwiają bezpośrednie Określanie wzorców bitowych zamiast używania notacji szesnastkowej.

## <a name="nullable-value-types"></a>Typy wartości dopuszczające wartość null

Typy wartości zwykłych nie mogą mieć wartości [null](language-reference/keywords/null.md). Można jednak utworzyć typy wartości null, umieszczając `?` po typie. Na przykład `int?` jest typem `int`, który może mieć również wartość [null](./language-reference/keywords/null.md). Typy wartości null są wystąpieniami typu struktury generycznej <xref:System.Nullable%601>. Typy wartości null są szczególnie przydatne podczas przekazywania danych do i z baz danych, w których wartości liczbowe mogą mieć wartość null lub być niezdefiniowane. Aby uzyskać więcej informacji, zobacz [typy wartości null](programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Zobacz także

- [Klasy](programming-guide/classes-and-structs/classes.md)
- [Typy podstawowe](basic-types.md)
