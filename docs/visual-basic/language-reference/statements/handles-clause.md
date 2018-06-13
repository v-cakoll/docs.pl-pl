---
title: Handles — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 15ce6a25aa5f403a2e55beb57b3693095743e52f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603720"
---
# <a name="handles-clause-visual-basic"></a>Handles — Klauzula (Visual Basic)
Deklaruje, że procedura obsługuje określone zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Części  
 `proceduredeclaration`  
 `Sub` Deklaracja procedury dla tej procedury, która obsłuży zdarzenie.  
  
 `eventlist`  
 Lista zdarzeń dla `proceduredeclaration` do obsługi, oddzielonych przecinkami. Zdarzenia musi zostać wywołane przez podstawową klasę dla bieżącej klasy lub za pomocą obiektu zadeklarowane za pomocą `WithEvents` — słowo kluczowe.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Handles` — słowo kluczowe na końcu deklaracji procedury, aby spowodować ich do obsługi zdarzenia generowane przez zmienną obiektu zadeklarowane za pomocą `WithEvents` — słowo kluczowe. `Handles` — Słowo kluczowe można również w klasie pochodnej do obsługi zdarzeń z klasy podstawowej.  
  
 `Handles` — Słowo kluczowe i `AddHandler` instrukcji zarówno umożliwiają określenie określone procedury obsługi zdarzeń w szczególności, że istnieją różnice. Użyj `Handles` — słowo kluczowe podczas definiowania procedury, aby określić, czy obsługuje ona określonego zdarzenia. `AddHandler` Instrukcji procedury łączy się z zdarzenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Dla zdarzeń niestandardowych aplikacji wywołuje zdarzenie `AddHandler` dostępu, gdy procedura dodawane jako program obsługi zdarzeń. Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 W poniższym przykładzie pokazano, jak używać klasy pochodnej `Handles` instrukcji obsługi zdarzenia z klasy podstawowej.  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera dwa przycisk obsługi zdarzeń **aplikacji WPF** projektu.  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest odpowiednikiem poprzedniego przykładu. `eventlist` w `Handles` klauzula zawiera zdarzenia dla obu przycisków.  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
