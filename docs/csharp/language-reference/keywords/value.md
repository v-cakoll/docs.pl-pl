---
title: value (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2501bc8964ed76534dba6c7cc519e095c57cb898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
