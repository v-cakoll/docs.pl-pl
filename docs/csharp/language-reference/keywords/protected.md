---
title: protected (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 2da8211ac21a5016478e7b881e7f2f9925b49cef
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001337"
---
# <a name="protected-c-reference"></a>protected (odwołanie w C#)
`protected` — Słowo kluczowe jest modyfikator dostępu składowej. 

 > Ta strona obejmuje `protected` dostępu. `protected` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) i [ `private protected` ](./private-protected.md) modyfikatorach dostępu. 

Chroniony element członkowski jest dostępny w ramach swojej klasy i wystąpienia klasy pochodnej. 

Porównanie `protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
  
## <a name="example"></a>Przykład  
 Chronione elementy członkowskie klasy bazowej jest dostępna w klasie pochodnej, tylko wtedy, gdy dostęp odbywa się przez typ klasy pochodnej. Na przykład rozważmy następujący segment kodu:  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 Wykonywanie instrukcji `a.x = 10` generuje błąd, ponieważ staje się wewnątrz metody statycznej Main, a nie jest wystąpieniem klasy B.  
  
 Składowe struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `DerivedPoint` jest tworzony na podstawie `Point`. W związku z tym dostęp chronionych elementów członkowskich klasy podstawowej, bezpośrednio z klasy pochodnej.  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 Jeśli zmienisz poziomy dostępu `x` i `y` do [prywatnej](../../../csharp/language-reference/keywords/private.md), kompilator zgłosi komunikaty o błędach:  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## 

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)  
- [Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))