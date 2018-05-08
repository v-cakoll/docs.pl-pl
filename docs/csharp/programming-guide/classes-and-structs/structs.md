---
title: Struktury (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
  
-   [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Instrukcje: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)
