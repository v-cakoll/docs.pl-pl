---
title: Handles, klauzula
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 2fecad919722f3da25c48f133a9c92b5e683d5e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345909"
---
# <a name="handles-clause-visual-basic"></a>Handles — Klauzula (Visual Basic)
Deklaruje, że procedura obsługuje określone zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Części  
 `proceduredeclaration`  
 Procedura `Sub` deklaracji procedury, która będzie obsługiwać zdarzenie.  
  
 `eventlist`  
 Lista zdarzeń `proceduredeclaration` do obsłużenia, rozdzielonych przecinkami. Zdarzenia muszą być wywoływane przez klasę bazową dla bieżącej klasy lub przez obiekt zadeklarowany za pomocą słowa kluczowego `WithEvents`.  
  
## <a name="remarks"></a>Uwagi  
 Użyj słowa kluczowego `Handles` na końcu deklaracji procedury, aby spowodować obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną za pomocą słowa kluczowego `WithEvents`. Słowa kluczowego `Handles` można również użyć w klasie pochodnej do obsługi zdarzeń z klasy bazowej.  
  
 Słowo kluczowe `Handles` i instrukcja `AddHandler` umożliwiają określenie, że konkretne procedury obsługują określone zdarzenia, ale istnieją różnice. Użyj słowa kluczowego `Handles` podczas definiowania procedury, aby określić, że obsługuje określone zdarzenie. Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [AddHandler instrukcji](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 W przypadku zdarzeń niestandardowych aplikacja wywołuje metodę dostępu `AddHandler` zdarzenia, gdy dodaje procedurę jako program obsługi zdarzeń. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 W poniższym przykładzie pokazano, jak Klasa pochodna może używać instrukcji `Handles`, aby obsłużyć zdarzenie z klasy bazowej.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera dwa programy obsługi zdarzeń przycisków dla projektu **aplikacji WPF** .  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest równoważny z poprzednim przykładem. `eventlist` w klauzuli `Handles` zawiera zdarzenia dla obu przycisków.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Zobacz także

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
