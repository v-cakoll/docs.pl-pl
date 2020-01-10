---
title: Jak napisać Konstruktor kopiujący — C# Przewodnik programistyczny
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714853"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Jak napisać Konstruktor kopiujący (C# Przewodnik programowania)
C#nie udostępnia konstruktora kopiującego dla obiektów, ale możesz napisać siebie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie [klasa](../../language-reference/keywords/class.md) `Person`definiuje Konstruktor kopiujący, który przyjmuje, jako argument, wystąpienie `Person`. Wartości właściwości argumentu są przypisywane do właściwości nowego wystąpienia `Person`. Kod zawiera alternatywny Konstruktor kopiujący, który wysyła `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ICloneable>
- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
