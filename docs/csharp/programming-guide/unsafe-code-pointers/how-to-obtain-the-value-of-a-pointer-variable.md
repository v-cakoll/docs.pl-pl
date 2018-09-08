---
title: 'Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 66f341e193a0f018adb76a40617f85266519e602
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138269"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)
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
  
**Wartość theChar = Z**
**adres theChar = 12F718**
**wartość pChar = Z**
**wartość Pinta = 90**

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
