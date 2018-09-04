---
title: value (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 1e120d68fc4a42f24feb225f652c14525fde3d71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521149"
---
# <a name="value-c-reference"></a>value (odwołanie w C#)
Kontekstowe słowo kluczowe `value` jest używany w metodzie dostępu set w deklaracji właściwości zwykłych. Jest on podobny do parametru wejściowego metody. Wyraz `value` odwołuje się do wartości, które podejmuje próbę przypisania do właściwości kodu klienta. W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name` , który używa `value` parametru, aby przypisać nowy ciąg do pola pomocniczego `name`. Z punktu widzenia kodu klienta operacji jest zapisywany jako przypisanie proste.  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 Aby uzyskać więcej informacji na temat użytkowania `value`, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
