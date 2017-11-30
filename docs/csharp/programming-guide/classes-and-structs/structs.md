---
title: "Struktury (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 475d9b96e078270faf6c841a62e6031556e8e539
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="structs-c-programming-guide"></a>Struktury (Przewodnik programowania w języku C#)
Struktury są zdefiniowane przy użyciu [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe, na przykład:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Struktury udziału większość takiej samej składni jak klasy, struktury są bardziej ograniczone niż klasy:  
  
-   W deklaracji struktury pól nie można zainicjować, chyba że zostały zgłoszone jako const lub statycznej.  
  
-   Struktury nie można zadeklarować konstruktora domyślnego (Konstruktor bez parametrów) lub finalizatora.  
  
-   Struktury są kopiowane na przypisanie. Gdy struktury jest przypisany do nowej zmiennej, wszystkie dane zostaną skopiowane, a wszelkie zmiany nowej kopii nie zmienia dane oryginał. Jest to ważne podczas pracy z kolekcjami typów wartości, takich jak słownik\<ciąg, myStruct >.  
  
-   Struktury są typy wartości i typy referencyjne występują następujące klasy.  
  
-   W przeciwieństwie do klasy, struktury można wdrożyć bez użycia `new` operatora.  
  
-   Struktury mogą zadeklarować konstruktorów, które mają parametry.  
  
-   Struktury nie może dziedziczyć z innego struktury lub klasy, a nie może być podstawą klasy. Strukturami dziedziczyć bezpośrednio po `System.ValueType`, który dziedziczy z `System.Object`.  
  
-   Struktury mogą implementować interfejsów.  
  
-   Struktury mogą być używane jako typ dopuszczający wartość null i można przypisać wartości null.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Używanie struktur](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Porady: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Porady: Implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)
