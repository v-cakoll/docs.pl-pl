---
title: 'Instrukcje: Uzyskiwanie wartości zmiennej wskaźnikowej - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 5fbc925b6770bc951a0d7ec856898f62c265462e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577157"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Instrukcje: Uzyskiwanie wartości zmiennej wskaźnikowej (C# Programming Guide)
Użyj operatora pośredniego wskaźnika można uzyskać zmiennej w lokalizacji wskazywanej przez kursor. Wyrażenie ma następującą postać, gdzie `p` jest typem wskaźnika:  
  
```  
*p;  
```  
  
 Jednoargumentowy operator pośredni nie można używać na wyrażeniu dowolnego typu innego niż typ wskaźnika. Ponadto nie można zastosować go do [void](../../../csharp/language-reference/keywords/void.md) wskaźnika.  
  
 Po zastosowaniu operatora pośredniego do [null](../../../csharp/language-reference/keywords/null.md) wskaźnika, wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zmienna typu `char` odbywa się za pomocą wskaźników różnego typu. Należy pamiętać, że adres `theChar` różnią się w celu uruchamiania, ponieważ można zmienić adresu fizycznego przydzielone do zmiennej.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
**Value of theChar = Z**
**Address of theChar = 12F718**
**Value of pChar = Z**
**Value of pInt = 90**

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
