---
title: fixed — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)
`fixed` Instrukcji uniemożliwia przemieszczanie zmienną ruchomy moduł garbage collector. `fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu. `Fixed`można również utworzyć [stały rozmiar buforów](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 `fixed` Instrukcja ustawia wskaźnik zarządzanych zmienną i "numerów PIN" zmiennej podczas wykonywania instrukcji. Bez `fixed`, wskaźników do zmiennych zarządzanych ruchome będzie znikomym ponieważ wyrzucanie elementów bezużytecznych można przenosić zmienne nieprzewidywalny. Kompilator języka C# tylko można przypisać wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 Wskaźnik można zainicjować za pomocą tablicy, ciąg, buforu o stałym rozmiarze lub adresu zmiennej. Poniższy przykład przedstawia użycie zmiennej adresów, tablic i ciągów. Aby uzyskać więcej informacji na temat bufory o ustalonym rozmiarze, zobacz [buforów o rozmiarze stałym](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 Należy zainicjować wielu wskaźników, jak długo będą tego samego typu.  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 Aby zainicjować wskaźników różnych typów, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 Po wykonaniu kodu w instrukcji zmiennych przypiętych są odpiąć i wyrzucanie elementów bezużytecznych. W związku z tym nie wskazują na tych zmiennych poza `fixed` instrukcji.  
  
> [!NOTE]
>  Nie można modyfikować wskaźników zainicjowany w instrukcjach "fixed".  
  
 W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty. Aby uzyskać więcej informacji, zobacz [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Bufory o ustalonym rozmiarze](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
