---
title: 'Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: 40a7ac34a4e68df7aa316adc3cbd1999d975eabe
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741883"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)
Aby uzyskać adres wyrażenie jednoargumentowe, co jest ewaluowane jako zmienna ustalona, należy użyć operatora address-of `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Operatora address-of może być tylko zastosowany do zmiennej. Jeśli zmienna jest zmienną ruchome, możesz użyć [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) tymczasowo naprawić zmiennej przed uzyskaniem adresu.  
  
 Jest odpowiedzialny za zapewnienie, że zmienna jest inicjowana. Kompilator nie wygeneruje komunikat o błędzie, jeśli zmienna nie jest zainicjowany.  
  
 Nie można pobrać adresu stała lub wartość.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie, wskaźnik do `int`, `p`i przypisanie adresu zmienną całkowitoliczbową `number`. Zmienna `number` jest inicjowana w wyniku przypisanie do `*p`. Jeśli komentarz wystąpi poza tym instrukcja przypisania inicjowania zmiennej `number` zostanie usunięty, ale błąd kompilacji nie jest zgłaszany.  

> [!NOTE]
> Skompilowania tego przykładu z [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
