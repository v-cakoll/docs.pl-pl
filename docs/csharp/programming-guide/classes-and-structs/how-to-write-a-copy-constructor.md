---
title: 'Instrukcje: Napisz Konstruktor kopiujący — C# Przewodnik programistyczny'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596608"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Instrukcje: Napisz Konstruktor kopiujący (C# Przewodnik programowania)
C#nie udostępnia konstruktora kopiującego dla obiektów, ale możesz napisać siebie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Person` [Klasa](../../language-reference/keywords/class.md) definiuje Konstruktor kopiujący, który przyjmuje, jako argument `Person`, wystąpienie. Wartości właściwości argumentu są przypisywane do właściwości nowego wystąpienia `Person`. Kod zawiera alternatywny Konstruktor kopiujący, który wysyła `Name` właściwości `Age` i wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ICloneable>
- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
