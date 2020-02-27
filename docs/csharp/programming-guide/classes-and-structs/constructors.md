---
title: Konstruktory C# — Przewodnik programowania
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626740"
---
# <a name="constructors-c-programming-guide"></a>Konstruktorzy (Przewodnik programowania w języku C#)

Za każdym razem, gdy tworzona jest [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/builtin-types/struct.md) , jego Konstruktor jest wywoływany. Klasa lub struktura może mieć wiele konstruktorów przyjmujących różne argumenty. Konstruktory umożliwiają programistom Ustawianie wartości domyślnych, ograniczenie tworzenia wystąpień i pisanie kodu, który jest elastyczny i łatwy do odczytania. Aby uzyskać więcej informacji i przykładów, zobacz [Używanie konstruktorów](./using-constructors.md) i [konstruktorów wystąpień](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Konstruktory bez parametrów
  
Jeśli nie podano konstruktora dla klasy, program C# tworzy jedną z nich domyślnie, tworząc wystąpienie obiektu i ustawia zmienne Członkowskie na wartości domyślne, jak wymieniono w [wartości domyślne C# typów](../../language-reference/builtin-types/default-values.md) artykułu. Jeśli nie podano konstruktora dla struktury, zależy on C# od *niejawnego konstruktora bez parametrów* , aby automatycznie inicjować każde pole do wartości domyślnej. Aby uzyskać więcej informacji i przykładów, zobacz [konstruktory wystąpień](instance-constructors.md).  

## <a name="constructor-syntax"></a>Składnia konstruktora

Konstruktor jest metodą, której nazwa jest taka sama jak nazwa jej typu. Podpis metody zawiera tylko nazwę metody i jej listę parametrów; nie zawiera typu zwracanego. Poniższy przykład pokazuje konstruktora dla klasy o nazwie `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Jeśli Konstruktor można zaimplementować jako pojedynczą instrukcję, można użyć [definicji treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md). W poniższym przykładzie zdefiniowano klasę `Location`, której Konstruktor ma jeden parametr ciągu o nazwie *name*. Definicja treści wyrażenia przypisuje argument do pola `locationName`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Konstruktory statyczne

W poprzednich przykładach są wyświetlane konstruktory wystąpień, które tworzą nowy obiekt. Klasa lub struktura może również mieć Konstruktor statyczny, który inicjuje statyczne elementy członkowskie typu.  Konstruktory statyczne są bezparametryczne. Jeśli nie postanowisz statycznego konstruktora do zainicjowania pól statycznych C# , kompilator inicjuje statyczne pola do ich wartości domyślnej, jak wymieniono w [wartości C# domyślne typów](../../language-reference/builtin-types/default-values.md) artykułu.

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
  
 [Jak napisać Konstruktor kopiujący](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Finalizatory](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Dlaczego inicjatory są uruchamiane w kolejności odwrotnej jako konstruktory? Część 1](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
