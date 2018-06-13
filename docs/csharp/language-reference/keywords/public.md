---
title: public (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 9bef5d076d9ab84aa15e2cdec2d176db8d1ac82b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171996"
---
# <a name="public-c-reference"></a>public (odwołanie w C#)
`public` — Słowo kluczowe jest modyfikator dostępu dla typów i członków typu. Dostęp publiczny jest najbardziej ograniczająca poziom dostępu. Nie ma żadnych ograniczeń na dostęp do publicznych członków, jak w poniższym przykładzie:  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) i [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie są deklarowane jako dwie klasy, `PointTest` i `MainClass`. Publiczne elementy członkowskie `x` i `y` z `PointTest` są dostępne bezpośrednio z `MainClass`.  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Jeśli zmienisz `public` poziom dostępu do [prywatnej](../../../csharp/language-reference/keywords/private.md) lub [chronione](../../../csharp/language-reference/keywords/protected.md), otrzymasz komunikat o błędzie:  
  
 "PointTest.y" jest niedostępny z powodu swojego poziomu ochrony.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
