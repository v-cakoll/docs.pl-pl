---
title: Struktury (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: abe39b336aa8e9aa7a8a8ee96ed6848804644ddd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518706"
---
# <a name="structs-c-programming-guide"></a>Struktury (Przewodnik programowania w języku C#)
Struktury są zdefiniowane przy użyciu [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe, na przykład:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Struktury udostępniać większość tej samej składni jak klasy, chociaż struktur są bardziej ograniczone niż klasy:  
  
-   W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.  
  
-   Domyślny konstruktor (Konstruktor bez parametrów), lub finalizator, nie można zadeklarować struktury.  
  
-   Struktury są kopiowane w przydziale. Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii. Ważne jest, aby pamiętać podczas pracy z kolekcjami typów wartości, takich jak słownik\<ciąg, myStruct >.  
  
-   Struktury są typami wartości i klasy są typami odwołań.  
  
-   W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.  
  
-   Struktury można zadeklarować konstruktorów, które mają parametry.  
  
-   Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy. Wszystkie struktury dziedziczyć bezpośrednio `System.ValueType`, który dziedziczy z `System.Object`.  
  
-   Struktura może zaimplementować interfejsów.  
  
-   Struktura może służyć jako typ dopuszczający wartość null i można przypisać wartości null.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Używanie struktur](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Instrukcje: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)
