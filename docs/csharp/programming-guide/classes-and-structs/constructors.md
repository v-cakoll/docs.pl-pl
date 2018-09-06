---
title: Konstruktorzy (Przewodnik programowania w języku C#)
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 3d07fe5f6164885a994838376887edccc260e291
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732689"
---
# <a name="constructors-c-programming-guide"></a>Konstruktorzy (Przewodnik programowania w języku C#)
Zawsze, gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzone, jego konstruktor jest wywoływany. Klasa lub struktura może mieć wiele konstruktorów, które przyjmują różne argumentów. Konstruktory Włącz programisty należy ustawić wartości domyślne, ograniczyć podczas tworzenia wystąpienia i napisać kod, który jest elastyczny i łatwy do odczytania. Aby uzyskać więcej informacji i przykładów, zobacz [korzystanie z konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) i [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="default-constructors"></a>Konstruktory domyślne
  
Jeśli nie podasz konstruktora dla klasy, C# tworzony jest jeden domyślny, który tworzy wystąpienie obiektu i ustawia zmienne składowe do wartości domyślnych, zgodnie z zaleceniami z [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Jeśli nie podasz konstruktora dla Twojej struktury, C# opiera się na *niejawnego domyślnego konstruktora* automatycznie zainicjować każdego pola typu wartości do wartości domyślnej, zgodnie z zaleceniami z [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Aby uzyskać więcej informacji i przykładów, zobacz [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Składnia konstruktora

Konstruktor jest metodą, którego nazwa jest taka sama jak nazwa ich typu. Jego podpis metody zawiera tylko nazwy metody i jego listy parametrów; nie ma typ zwracany. W poniższym przykładzie pokazano konstruktora dla klasy o nazwie `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Jeśli Konstruktor można zaimplementować jako pojedynczej instrukcji, można użyć [definicja treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md). W poniższym przykładzie zdefiniowano `Location` klasy, której Konstruktor ma jeden ciąg parametr o nazwie *nazwa*. Definicja treści wyrażenia przypisuje argument `locationName` pola.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Konstruktory statyczne

Poprzednie przykłady ma wszystkie konstruktory pokazywane wystąpienie, które tworzą nowy obiekt. Klasa lub struktura może być również statyczny Konstruktor inicjuje statyczne elementy członkowskie tego typu.  Konstruktory statyczne są bez parametrów. Jeśli nie podasz konstruktora statycznego zainicjować pola statyczne, kompilator języka C# będzie dostarczać statycznego konstruktora domyślnego i inicjuje pola statyczne, aby przywrócić wartości domyślne, zgodnie z zaleceniami z [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). 

W poniższym przykładzie użyto statycznego konstruktora zainicjować pole statyczne.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Można również zdefiniować Konstruktor statyczny przy użyciu definicji treści wyrażenia, co ilustruje poniższy przykład. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Aby uzyskać więcej informacji i przykładów, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Instrukcje: zapisywanie konstruktora kopiowania](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [static](../../../csharp/language-reference/keywords/static.md)  
- [Dlaczego są inicjatory uruchamiane w kolejności przeciwnej jako konstruktory? Część 1](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
