---
title: partial (typ) (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4f57149dd18deb08aa11b72d0a6d5f71b3838bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266692"
---
# <a name="partial-type-c-reference"></a>partial (typ) (odwołanie w C#)
Definicje typu częściowego umożliwiają definicji klasy, struktury lub interfejsu można podzielić na wiele plików.  
  
 W File1.cs:  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 W deklaracji File2.cs:  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 Dzielenie klasy, struktury lub interfejsu typu przez kilka plików może być przydatne podczas pracy z dużych projektów lub automatycznie wygenerowanego kodu, takim jak udostępniany przez [Projektant formularzy systemu Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Typ częściowego może zawierać [metody częściowej](../../../csharp/language-reference/keywords/partial-method.md). Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)
