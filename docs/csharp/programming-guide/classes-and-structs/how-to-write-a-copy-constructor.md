---
title: Jak napisać konstruktora kopii - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714853"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Jak napisać konstruktora kopii (C# Programming Guide)
C# nie udostępnia konstruktora kopiowania dla obiektów, ale można napisać samodzielnie.  
  
## <a name="example"></a>Przykład  
 W poniższym `Person`przykładzie [klasa](../../language-reference/keywords/class.md) definiuje konstruktora kopiowania, który `Person`przyjmuje, jako jego argument, wystąpienie . Wartości właściwości argumentu są przypisane do właściwości nowego wystąpienia . `Person` Kod zawiera konstruktora kopiowania alternatywnego, który wysyła `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ICloneable>
- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizatory](./destructors.md)
