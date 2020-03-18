---
title: Konstruktorzy — przewodnik programowania Języka C#
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399792"
---
# <a name="constructors-c-programming-guide"></a>Konstruktorzy (Przewodnik programowania w języku C#)

Za każdym razem, gdy tworzona jest [klasa](../../language-reference/keywords/class.md) lub [struktura,](../../language-reference/builtin-types/struct.md) jego konstruktor jest wywoływany. Klasa lub struktura może mieć wiele konstruktorów, które przyjmują różne argumenty. Konstruktorzy umożliwiają programisty ustawienie wartości domyślnych, ograniczenie wystąpienia i zapiskodu, który jest elastyczny i łatwy do odczytania. Aby uzyskać więcej informacji i przykłady, zobacz [Korzystanie z konstruktorów](./using-constructors.md) i [konstruktorów wystąpień](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Konstruktory bez parametrów
  
Jeśli nie podasz konstruktora dla klasy, C# tworzy domyślnie jeden, który tworzy obiekt i ustawia zmienne członkowskie do wartości domyślnych, jak wymienione w [wartości domyślne c# typy](../../language-reference/builtin-types/default-values.md) artykułu. Jeśli nie podasz konstruktora dla struktury, C# opiera się na *niejawnykonstruktor bezparametrów,* aby automatycznie zainicjować każde pole do jego wartości domyślnej. Aby uzyskać więcej informacji i przykłady, zobacz [Konstruktory wystąpienia](instance-constructors.md).  

## <a name="constructor-syntax"></a>Składnia konstruktora

Konstruktor jest metodą, której nazwa jest taka sama jak nazwa jego typu. Jego podpis metody zawiera tylko nazwę metody i jej listę parametrów; nie zawiera typu zwracanego. W poniższym przykładzie przedstawiono konstruktora dla klasy o nazwie `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Jeśli konstruktor może być zaimplementowany jako pojedyncza instrukcja, można użyć [definicji treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md). Poniższy przykład definiuje `Location` klasę, której konstruktor ma parametr pojedynczego ciągu *o*nazwie . Definicja treści wyrażeń `locationName` przypisuje argument do pola.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Konstruktory statyczne

Poprzednie przykłady mają wszystkie pokazane konstruktory wystąpienia, które tworzą nowy obiekt. Klasa lub struktura może mieć również konstruktora statycznego, który inicjuje statyczne elementy członkowskie typu.  Konstruktory statyczne są bezparametrowe. Jeśli konstruktor statyczny nie zostanie zainicjowany przez konstruktor statyczny, kompilator Języka C# inicjuje pola statyczne do ich wartości domyślnej, jak wymieniono w artykule [Wartości domyślne typów Języka C#.](../../language-reference/builtin-types/default-values.md)

W poniższym przykładzie użyto konstruktora statycznego do zainicjowania pola statycznego.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Można również zdefiniować konstruktora statycznego z definicji treści wyrażenia, jak pokazano w poniższym przykładzie.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Aby uzyskać więcej informacji i przykładów, zobacz [Konstruktora statyczne](./static-constructors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie konstruktorów](./using-constructors.md)  
  
 [Konstruktory wystąpień](./instance-constructors.md)  
  
 [Konstruktory prywatne](./private-constructors.md)  
  
 [Konstruktory statyczne](./static-constructors.md)  
  
 [Porada: zapisywanie konstruktora kopiującego](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Finalizatory](./destructors.md)
- [Statyczne](../../language-reference/keywords/static.md)
- [Dlaczego inicjatorzy działają w odwrotnym porządku jako konstruktorzy? Część pierwsze](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
