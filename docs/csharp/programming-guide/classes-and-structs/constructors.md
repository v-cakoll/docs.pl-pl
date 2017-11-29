---
title: "Konstruktorzy (Przewodnik programowania w języku C#)"
ms.date: 05/05/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 65c50311548667ab5fdc685b70b6ab9e88376067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="constructors-c-programming-guide"></a>Konstruktorzy (Przewodnik programowania w języku C#)
Zawsze, gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzona, jest nazywany jego konstruktora. Klasy lub struktury może mieć wiele konstruktorów przyjmujących różnych argumentów. Konstruktory Włącz programisty ustawić wartości domyślne, ograniczyć wystąpienia i pisania kodu, który jest elastyczny i łatwy do odczytania. Aby uzyskać dodatkowe informacje i przykłady, zobacz [za pomocą konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) i [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="default-constructors"></a>Konstruktory domyślne
  
Jeśli nie podasz konstruktora dla klasy, C# tworzy domyślnie tworzy wystąpienie obiektu, który ustawia wartości domyślne zmienne Członkowskie wymienionych w [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Jeśli nie podasz konstruktora dla Twojego struktury, C# zależy od *niejawne domyślnego konstruktora* automatycznie zainicjować każdego pola typu wartości na wartość domyślną wymienionych w [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). Aby uzyskać dodatkowe informacje i przykłady, zobacz [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  

## <a name="constructor-syntax"></a>Składni konstruktora

Konstruktor jest metoda, którego nazwa jest taka sama jak nazwa ich typu. Podpis metody zawiera nazwę metody i jej listy parametrów; nie ma zwracanego typu. W poniższym przykładzie przedstawiono konstruktora dla klasy o nazwie `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Jeśli za pomocą jednej instrukcji można implementować konstruktora, możesz użyć [definicja treść wyrażenia](../statements-expressions-operators/expression-bodied-members.md). W poniższym przykładzie zdefiniowano `Location` klasy, których Konstruktor ma jeden ciąg parametru o nazwie *nazwa*. Definicja treść wyrażenia przypisuje argument `locationName` pola.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Konstruktory statyczne

Poprzednich przykładach ma wszystkie konstruktory wystąpień pokazano, co spowoduje utworzenie nowego obiektu. Klasy lub struktury ma także statycznego konstruktora, który inicjuje statyczne elementy członkowskie tego typu.  Konstruktory statyczne są bez parametrów. Jeśli nie podasz Konstruktor statyczny zainicjować pól statycznych, kompilator języka C# będzie dostarczać statycznego konstruktora domyślnego i inicjuje pola statyczne przywrócić wartości domyślne, których listę zamieszczono w [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). 

W poniższym przykładzie użyto Konstruktor statyczny zainicjować pola statycznego.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Można również zdefiniować Konstruktor statyczny z definicją treść wyrażenia, jak przedstawiono na poniższym przykładzie. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Aby uzyskać dodatkowe informacje i przykłady, zobacz [konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [Konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [Konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [Konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [Porady: zapisywanie konstruktora kopiującego](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [statyczne](../../../csharp/language-reference/keywords/static.md)  
 [Dlaczego są inicjatory uruchamiane w kolejności przeciwną jako konstruktorów? Część 1](http://go.microsoft.com/fwlink/?LinkId=112374)
