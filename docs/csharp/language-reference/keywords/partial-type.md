---
title: partial (typ) (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 362a02815cb249d57c0bd19706714df1d71644f4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929666"
---
# <a name="partial-type-c-reference"></a>partial (typ) (odwołanie w C#)
Definicje typu częściowego umożliwiają definicji klasy, struktury lub interfejsu ma być podzielony na wiele plików.  
  
 W File1.cs:  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 W File2.cs deklaracji:  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 Podział klasy, struktury lub interfejsu typ za pośrednictwem kilku plików może być przydatny podczas pracy z dużymi projektami lub z automatycznie wygenerowanego kodu, takim jak udostępniany przez [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Może zawierać typu częściowego [metody częściowej](../../../csharp/language-reference/keywords/partial-method.md). Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)
