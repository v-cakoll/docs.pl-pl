---
title: "Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)
Operator pośredni wskaźnik umożliwia uzyskanie zmiennej w lokalizacji wskazywanej przez kursor. Wyrażenie ma następującą postać, gdzie `p` jest typem wskaźnika:  
  
```  
*p;  
```  
  
 Nie można użyć operatora jednoargumentowego operatora pośredniego na wyrażeniu dowolnego typu, innego niż typ wskaźnika. Ponadto nie można zastosować go do [void](../../../csharp/language-reference/keywords/void.md) wskaźnika.  
  
 Po zastosowaniu operator pośredni do [null](../../../csharp/language-reference/keywords/null.md) wskaźnika, wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zmienna typu `char` uzyskuje się dostęp za pomocą wskaźniki różnych typów. Należy pamiętać, że adres `theChar` różni się od do rozpoczęcia realizacji, nie można zmienić adresu fizycznego przydzielone do zmiennej.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 **Wartość theChar = Z**  
**Adres theChar = 12F718**  
**Wartość pChar = Z**   
**Wartość Pinta = 90**    
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy wskaźnika](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Fixed — instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
