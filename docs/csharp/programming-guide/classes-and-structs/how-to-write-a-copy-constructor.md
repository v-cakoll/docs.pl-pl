---
title: 'Porady: zapisywanie konstruktora kopiującego (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 8a7cc85d40272918f4839d13fcccb79b558eeac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322500"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Porady: zapisywanie konstruktora kopiującego (Przewodnik programowania w języku C#)
C# nie zapewnia Konstruktor kopiujący dla obiektów, ale można wpisać własny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako jej argument wystąpienia `Person`. Wartości właściwości argumentu są przypisane do właściwości nowe wystąpienie klasy `Person`. Kod zawiera Konstruktor kopiujący alternatywnych, która wysyła `Name` i `Age` właściwości wystąpienia, który ma zostać skopiowany do konstruktora wystąpienia klasy.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ICloneable>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
