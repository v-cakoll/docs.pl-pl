---
title: Struktury — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: df2a235651a2242ffe18df377dce9995af31e99f
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392454"
---
# <a name="structs-c-programming-guide"></a>Struktury (Przewodnik programowania w języku C#)

Struktury są zdefiniowane za pomocą słowa kluczowego [struct](../../language-reference/keywords/struct.md) , na przykład:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Struktury współużytkują większość tej samej składni co klasy. Nazwa struktury musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md). Struktury są bardziej ograniczone niż klasy w następujący sposób:  
  
- W deklaracji struktury nie można inicjować pól, chyba że są one zadeklarowane jako const lub static.  
- Struktura nie może deklarować bezparametrowego konstruktora (Konstruktor bez parametrów) lub finalizatora.  
- Struktury są kopiowane podczas przypisywania. Gdy struktura jest przypisana do nowej zmiennej, wszystkie dane są kopiowane i wszelkie modyfikacje nowej kopii nie zmieniają danych dla oryginalnej kopii. Jest to ważne, aby pamiętać, że podczas pracy z kolekcjami typów wartości, takimi jak `Dictionary<string, myStruct>`.  
- Struktury są typami wartości, w przeciwieństwie do klas, które są typami referencyjnymi.  
- W przeciwieństwie do klas, struktury mogą być tworzone bez użycia operatora `new`.  
- Struktury mogą deklarować konstruktory z parametrami.
- Struktura nie może dziedziczyć z innej struktury lub klasy i nie może być podstawą klasy. Wszystkie struktury dziedziczą bezpośrednio z <xref:System.ValueType>, które dziedziczy po <xref:System.Object>.  
- Struktura może implementować interfejsy.
- Struktura nie może być `null` i nie można przypisać zmiennej struktury `null`, chyba że zmienna jest zadeklarowana jako typ wartości null.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](index.md)
- [Klasy](classes.md)
- [Typy wartości null](../nullable-types/index.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Używanie struktur](using-structs.md)
- [Instrukcje: Zapoznaj się z różnicą między przekazywaniem struktury i przekazywaniem odwołania do klasy do metody @ no__t-0
