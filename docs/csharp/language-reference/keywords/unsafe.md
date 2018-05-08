---
title: unsafe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 367a080cf58514b3ffcc30c17d8fe7bb07e0e9ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="unsafe-c-reference"></a>unsafe (odwołanie w C#)
`unsafe` — Słowo kluczowe oznacza niebezpiecznym kontekście, który jest wymagany do żadnej operacji obejmujący wskaźniki. Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 Można użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego. W związku z tym niebezpiecznym kontekście jest uważany za cały zakres tekstowa typu lub elementu członkowskiego. Na przykład poniżej przedstawiono metody zadeklarowanej z `unsafe` modyfikator:  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Zakres niebezpiecznym kontekście rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 Blok niebezpieczny umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku. Na przykład:  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Aby skompilować kod niezabezpieczony, należy określić [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora. Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Bufory o ustalonym rozmiarze](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
