---
title: "Implements — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a>Implements — Klauzula (Visual Basic)
Wskazuje, że element członkowski klasy lub struktury dostarcza implementację dla elementu członkowskiego zdefiniowanego w interfejsie.  
  
## <a name="remarks"></a>Uwagi  
`Implements` — Słowo kluczowe nie jest taka sama jak [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md). Możesz użyć `Implements` instrukcji, aby określić, że klasy lub struktury implementuje co najmniej jeden interfejs, a następnie dla każdego elementu członkowskiego możesz użyć `Implements` — słowo kluczowe, aby określić, które interfejs i który element członkowski implementuje.

Jeśli klasy lub struktury implementuje interfejs, musi on zawierać `Implements` instrukcji natychmiast po [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) lub [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md), i musi on implementować wszystkie elementy członkowskie zdefiniowane przez interfejs.

## <a name="reimplementation"></a>Ponowna implementacja  
W klasie pochodnej można reimplement elementu członkowskiego interfejsu, która już została zaimplementowana klasy podstawowej. Różni się to od zastępowania elementu członkowskiego klasy podstawowej w następujących aspektach:

- Element członkowski klasy podstawowej muszą być [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) do można reimplemented.
- Można reimplement elementu członkowskiego z inną nazwą.

`Implements` — Słowo kluczowe może być używana w następujących sytuacjach:
- [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
