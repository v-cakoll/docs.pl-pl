---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2f7bdba4b01bd307e0c52802509669f772b5eb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać zastąpiony w klasie pochodnej, zanim będzie można go używać.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `MustOverride` tylko w instrukcji deklaracji właściwość lub procedura. Właściwość lub procedura, która określa `MustOverride` musi być elementem członkowskim klasy, i muszą być oznaczone jako klasa [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Deklaracja niekompletne.** Po określeniu `MustOverride`, wszelkie dodatkowe wiersze kodu właściwość lub procedura, nie zostanie podana nie nawet `End Function`, `End Property`, lub `End Sub` instrukcji.  
  
-   **Łączna modyfikatorów.** Nie można określić `MustOverride` razem z `NotOverridable`, `Overridable`, lub `Shared` w tej samej deklaracji.  
  
-   **Przesłanianiem i zastępowaniem.** Zarówno przesłanianiem i zastępowaniem ponownego zdefiniowania odziedziczonego elementu, ale są istotne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Alternatywne warunki.** Element, której nie można użyć z wyjątkiem zastąpienia jest czasami nazywany *czystej wirtualnej* elementu.  
  
 `MustOverride` Modyfikatora można używać w tych sytuacjach:  
  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Możliwym do zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
