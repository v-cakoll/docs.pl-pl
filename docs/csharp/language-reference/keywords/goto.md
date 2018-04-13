---
title: goto (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a>goto (odwołanie w C#)
`goto` Instrukcji przesyła formantu programu bezpośrednio z etykietą instrukcji.  
  
 Typowym zastosowaniem `goto` się transfer kontroli do określonej etykiety przypadek switch lub etykieta domyślna w `switch` instrukcji.  
  
 `goto` Instrukcji przydaje się także wykorzystanie głęboko zagnieżdżone pętle.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, za pomocą `goto` w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji.  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, przy użyciu `goto` umożliwiające rozbicie z pętli zagnieżdżonych.  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [goto — instrukcja](/cpp/cpp/goto-statement-cpp)  
 [Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)
