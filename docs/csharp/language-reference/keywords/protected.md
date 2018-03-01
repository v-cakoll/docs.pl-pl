---
title: "protected (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 18278ed28f899d9030d6056eca9bbe83ebec04c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="protected-c-reference"></a>protected (odwołanie w C#)
`protected` — Słowo kluczowe jest modyfikator dostępu elementu członkowskiego. 

 > Ta strona zawiera `protected` dostępu. `protected` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) i [ `private protected` ](./private-protected.md) modyfikatorów dostępu. 

Chroniony element członkowski jest dostępny w swojej klasie i wystąpień klasy pochodnej. 

Porównanie `protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
  
## <a name="example"></a>Przykład  
 Chroniony element członkowski klasy podstawowej jest dostępna w klasie pochodnej, tylko wtedy, gdy występuje dostęp za pośrednictwem typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 Instrukcja `a.x = 10` generuje błąd, ponieważ jest on w statycznej metody Main, a nie jest wystąpieniem klasy B.  
  
 Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `DerivedPoint` jest pochodną `Point`. W związku z tym dostępne chronionych elementów członkowskich klasy podstawowej bezpośrednio z klasy pochodnej.  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 Zmiana poziomów dostępu `x` i `y` do [prywatnej](../../../csharp/language-reference/keywords/private.md), kompilator będzie wystawiać komunikaty o błędach:  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [publiczny](../../../csharp/language-reference/keywords/public.md)  
 [prywatne](../../../csharp/language-reference/keywords/private.md)  
 [wewnętrzny](../../../csharp/language-reference/keywords/internal.md)  
 [Problemy z zabezpieczeniami dla wewnętrznego wirtualnego słowa kluczowe](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))