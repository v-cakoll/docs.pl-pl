---
title: 'Instrukcje: Zapisywanie konstruktora kopiującego - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 169bdfc53d0c30ffc14e5a9525920679a94fbf23
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982144"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Instrukcje: Zapisywanie konstruktora kopiującego (C# Programming Guide)
C# nie zapewnia konstruktorowi kopii dla obiektów, ale możesz napisać ją sam.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako argument, wystąpienie `Person`. Wartości właściwości argumentu są przypisywane właściwościom nowego wystąpienia programu `Person`. Kod zawiera alternatywny Konstruktor kopiujący wysyłający `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ICloneable>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
