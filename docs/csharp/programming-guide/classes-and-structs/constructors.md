---
title: Konstruktory — Przewodnik programowania w języku C#
description: Konstruktor w języku C# jest wywoływany, gdy tworzona jest Klasa lub struktura. Używaj konstruktorów, aby ustawiać wartości domyślne, ograniczać Tworzenie wystąpień i pisać elastyczne, czytelne kod.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 4a731e648143f5e0ecf8860625962d8baa29fe26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474907"
---
# <a name="constructors-c-programming-guide"></a>Konstruktorzy (Przewodnik programowania w języku C#)

Za każdym razem, gdy tworzona jest [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/builtin-types/struct.md) , jego Konstruktor jest wywoływany. Klasa lub struktura może mieć wiele konstruktorów przyjmujących różne argumenty. Konstruktory umożliwiają programistom Ustawianie wartości domyślnych, ograniczenie tworzenia wystąpień i pisanie kodu, który jest elastyczny i łatwy do odczytania. Aby uzyskać więcej informacji i przykładów, zobacz [Używanie konstruktorów](./using-constructors.md) i [konstruktorów wystąpień](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Konstruktory bez parametrów
  
Jeśli nie podajesz konstruktora dla klasy, w języku C# domyślnie zostanie utworzona jedna z nich, która tworzy wystąpienie obiektu i ustawia zmienne Członkowskie na wartości domyślne, zgodnie z [wartościami domyślnymi w artykule typy C#](../../language-reference/builtin-types/default-values.md) . Jeśli nie podano konstruktora dla struktury, C# opiera się na *niejawnym konstruktorze bez parametrów* , aby automatycznie inicjować każde pole do wartości domyślnej. Aby uzyskać więcej informacji i przykładów, zobacz [konstruktory wystąpień](instance-constructors.md).  

## <a name="constructor-syntax"></a>Składnia konstruktora

Konstruktor jest metodą, której nazwa jest taka sama jak nazwa jej typu. Podpis metody zawiera tylko nazwę metody i jej listę parametrów; nie zawiera typu zwracanego. Poniższy przykład pokazuje konstruktora dla klasy o nazwie `Person` .

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Jeśli Konstruktor można zaimplementować jako pojedynczą instrukcję, można użyć [definicji treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md). W poniższym przykładzie zdefiniowano `Location` klasę, której Konstruktor ma jeden parametr ciągu o nazwie *name*. Definicja treści wyrażenia przypisuje argument do `locationName` pola.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Konstruktory statyczne

W poprzednich przykładach są wyświetlane konstruktory wystąpień, które tworzą nowy obiekt. Klasa lub struktura może również mieć Konstruktor statyczny, który inicjuje statyczne elementy członkowskie typu.  Konstruktory statyczne są bezparametryczne. Jeśli nie postanowisz statycznego konstruktora do zainicjowania pól statycznych, kompilator języka C# inicjuje statyczne pola do ich wartości domyślnej, jak wymieniono w [domyślnych wartościach typu C#](../../language-reference/builtin-types/default-values.md) artykułu.

Poniższy przykład używa konstruktora statycznego, aby zainicjować pole statyczne.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Można również zdefiniować statyczny Konstruktor z definicją treści wyrażenia, jak pokazano w poniższym przykładzie.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Aby uzyskać więcej informacji i przykładów, zobacz [statyczne konstruktory](./static-constructors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie konstruktorów](./using-constructors.md)  
  
 [Konstruktory wystąpień](./instance-constructors.md)  
  
 [Konstruktory prywatne](./private-constructors.md)  
  
 [Konstruktory statyczne](./static-constructors.md)  
  
 [Porada: zapisywanie konstruktora kopiującego](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Finalizatory](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Dlaczego inicjatory są uruchamiane w kolejności odwrotnej jako konstruktory? Część 1](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
