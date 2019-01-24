---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: dbcd0625cdbcd06affc495ca29972c6c183c10f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582116"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)
Określa, że właściwość lub procedura przesłania właściwość o identycznej nazwie lub dziedziczone z klasy bazowej procedury.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Możesz użyć `Overrides` tylko w instrukcji deklaracji właściwość lub procedura.  
  
-   **Modyfikatory połączone.** Nie można określić `Overrides` wraz z `Shadows` lub `Shared` w tej samej deklaracji. Ponieważ element nadrzędnych jest niejawnie możliwym do zastąpienia, nie można połączyć `Overridable` z `Overrides`.  
  
-   **Podpisów dopasowania.** Podpis tej deklaracji musi dokładnie odpowiadać *podpisu* właściwość lub procedurę, która zastępuje ona. Oznacza to, list parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, z tymi samymi typami danych.  
  
     Oprócz podpisu nadrzędnych deklaracji musi również dokładnie odpowiadać następujące czynności:  
  
    -   Poziom dostępu  
  
    -   Typ zwracany, jeśli istnieje  
  
-   **Sygnatur ogólnych.** Procedury ogólne podpis zawiera liczbę parametrów typu. W związku z tym nadrzędnych deklaracja musi odpowiadać wersją klasy bazowej, w tym zakresie, a także.  
  
-   **Dodatkowe dopasowywania.** Oprócz dopasowania podpis wersją klasy bazowej, ta deklaracja musi być również zgodna go pod następującymi względami:  
  
    -   Modyfikator poziom dostępu (takich jak [publicznych](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Przekazywanie mechanizm każdego parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Ograniczenie listy dla każdego parametru typu ogólnego procedury  
  
-   **Przesłanianiem i zastępowaniem.** Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby pracować z interfejsów API biblioteki C# łatwiejsze.  
  
 `Overrides` Modyfikator mogą być używane w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
