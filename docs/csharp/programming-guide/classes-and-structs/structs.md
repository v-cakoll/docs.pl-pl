---
title: Struktury - C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 063d7e3b68fbe6c01ff0df4ae935fec5af6f6891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743835"
---
# <a name="structs-c-programming-guide"></a>Struktury (Przewodnik programowania w języku C#)

Struktury są zdefiniowane przy użyciu [struktury](../../language-reference/keywords/struct.md) — słowo kluczowe, na przykład:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Struktury współużytkując większość tej samej składni jako klasy. Nazwa struktury musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md). Struktury są bardziej ograniczone niż klas w następujący sposób:  
  
- W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.  
- Struktura nie można zadeklarować konstruktora bez parametrów (Konstruktor bez parametrów) lub finalizatora.  
- Struktury są kopiowane w przydziale. Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii. Ważne jest, aby pamiętać podczas pracy z kolekcjami wartość typy takie jak `Dictionary<string, myStruct>`.  
- Struktury są typami wartości, w przeciwieństwie do klasy, które są typami odwołań.  
- W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.  
- Struktury można zadeklarować konstruktorów, które mają parametry.
- Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy. Wszystkie struktury dziedziczyć bezpośrednio <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.  
- Struktura może zaimplementować interfejsów.
- Struktura nie może być `null`, i nie można przypisać zmiennej struktury `null` chyba, że zmienna jest zadeklarowana jako typ dopuszczający wartość null.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](index.md)
- [Klasy](classes.md)
- [Typy dopuszczające wartości null](../nullable-types/index.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Używanie struktur](using-structs.md)
- [Instrukcje: Różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
