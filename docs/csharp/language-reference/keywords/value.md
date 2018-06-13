---
title: value (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: c8f808540385552f6222566f23251f6cbd6e86df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265275"
---
# <a name="value-c-reference"></a>value (odwołanie w C#)
Kontekstowe słowo kluczowe `value` jest używany w metodzie dostępu set w deklaracjach zwykłej właściwości. Jest on podobny do parametru wejściowego dla metody. Wyraz `value` odwołuje się do wartości, który próbuje kod klienta można przypisać do właściwości. W poniższym przykładzie `MyDerivedClass` ma właściwość o nazwie `Name` używającą `value` parametr, aby przypisać nowe parametry do pola zapasowy `name`. Z punktu widzenia kodu klienta operacji są zapisywane jako przypisanie proste.  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 Aby uzyskać więcej informacji o wykorzystaniu `value`, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
