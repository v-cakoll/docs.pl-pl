---
title: 'Porady: uzyskiwanie wartości zmiennej wskaźnikowej - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 9a10bcc809f3ecbc9a0fa9b917940b8e030fab8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635104"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Porady: uzyskiwanie wartości zmiennej wskaźnikowej (C# Programming Guide)

Użyj operatora pośredniego wskaźnika można uzyskać zmiennej w lokalizacji wskazywanej przez kursor. Wyrażenie ma następującą postać, gdzie `p` jest typem wskaźnika:  

```csharp
*p;  
```

Jednoargumentowy operator pośredni nie można używać na wyrażeniu dowolnego typu innego niż typ wskaźnika. Ponadto nie można zastosować go do [void](../../../csharp/language-reference/keywords/void.md) wskaźnika.  

Po zastosowaniu operatora pośredniego do [null](../../../csharp/language-reference/keywords/null.md) wskaźnika, wynik zależy od implementacji.  

## <a name="example"></a>Przykład

W poniższym przykładzie zmienna typu `char` odbywa się za pomocą wskaźników różnego typu. Należy pamiętać, że adres `theChar` różnią się w celu uruchamiania, ponieważ można zmienić adresu fizycznego przydzielone do zmiennej.  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
**Wartość theChar = Z**  
**Adres theChar = 12F718**  
**Wartość pChar = Z**  
**Wartość Pinta = 90**  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
