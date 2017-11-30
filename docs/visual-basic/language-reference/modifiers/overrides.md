---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1bee6a6235b87a7e20f087a73bef76e0fc7bf124
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)
Określa, że właściwość lub procedura przesłania o identycznej nazwie właściwość lub procedura dziedziczona z klasy podstawowej.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Overrides` tylko w instrukcji deklaracji właściwość lub procedura.  
  
-   **Łączna modyfikatorów.** Nie można określić `Overrides` razem z `Shadows` lub `Shared` w tej samej deklaracji. Zastępowanie elementu jest niejawnie możliwym do zastąpienia, nie można łączyć `Overridable` z `Overrides`.  
  
-   **Dopasowywanie podpisów.** Podpis tej deklaracji musi dokładnie odpowiadać *podpisu* właściwości lub procedury, która zastępuje on. Oznacza to, listy parametrów muszą mieć taką samą liczbę parametrów, w takiej samej kolejności, z tymi samymi typami danych.  
  
     Oprócz podpisu Zastępowanie deklaracji musi również dokładnie odpowiadać następujące czynności:  
  
    -   Poziom dostępu  
  
    -   Typ zwracany, jeśli istnieje  
  
-   **Ogólny podpisów.** Procedury ogólne podpis zawiera liczbę parametrów typu. W związku z tym zastępowanie deklaracja musi odpowiadać wersji klasy podstawowej w tym zakresie, a także.  
  
-   **Dodatkowe dopasowania.** Oprócz dopasowania podpis wersji klasę podstawową, ta deklaracja musi być również zgodna go w następujących aspektach:  
  
    -   Modyfikator dostępu na poziomie (takich jak [publicznego](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Przekazywanie mechanizmem poszczególnych parametrów ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Ograniczenie listy dla każdego parametru typu ogólnego procedury  
  
-   **Przesłanianiem i zastępowaniem.** Zarówno przesłanianiem i zastępowaniem ponownego zdefiniowania odziedziczonego elementu, ale są istotne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` , aby pracować z C# łatwiej biblioteki interfejsów API.  
  
 `Overrides` Modyfikatora można używać w tych sytuacjach:  
  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Możliwym do zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
