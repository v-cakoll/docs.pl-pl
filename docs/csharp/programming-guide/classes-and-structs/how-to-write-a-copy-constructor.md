---
title: 'Instrukcje: Zapisywanie konstruktora kopiującego - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 252e66229b75c545c85aa175267ea267c138a087
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573127"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Instrukcje: Zapisywanie konstruktora kopiującego (C# Programming Guide)
C# nie zapewnia konstruktorowi kopii dla obiektów, ale możesz napisać ją sam.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako argument, wystąpienie `Person`. Wartości właściwości argumentu są przypisywane właściwościom nowego wystąpienia programu `Person`. Kod zawiera alternatywny Konstruktor kopiujący wysyłający `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ICloneable>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
