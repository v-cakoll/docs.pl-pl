---
title: Handles — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 50a449ea8a5131c878cf703f44695cd2e2304444
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842580"
---
# <a name="handles-clause-visual-basic"></a>Handles — Klauzula (Visual Basic)
Deklaruje, że procedura obsługuje określone zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Części  
 `proceduredeclaration`  
 `Sub` Deklaracja procedury dla procedury, która obsłuży zdarzenie.  
  
 `eventlist`  
 Lista zdarzeń dla `proceduredeclaration` do obsługi, oddzielonych przecinkami. Zdarzenia musi zostać wywołane, albo klasę bazową dla bieżącej klasy lub obiekt, który został zadeklarowany za pomocą `WithEvents` — słowo kluczowe.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Handles` — słowo kluczowe na końcu deklaracja procedury, aby spowodować, że obsługa zdarzeń wywołanych przez zmienną obiektu zadeklarowane za pomocą `WithEvents` — słowo kluczowe. `Handles` — Słowo kluczowe można również w klasie pochodnej do obsługi zdarzeń z klasy bazowej.  
  
 Zarówno słowo kluczowe `Handles`, jak i instrukcja `AddHandler` umożliwiają określenie konkretnych procedur do obsługi konkretnych zdarzeń, ale występują tu pewne różnice. Słowa kluczowego `Handles` należy użyć podczas definiowania procedury, aby określić, że ma ona obsługiwać konkretne zdarzenie. Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Dla zdarzenia niestandardowe, aplikacja wywołuje zdarzenie `AddHandler` dostępu, jeśli zwiększy procedury jako program obsługi zdarzeń. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 W poniższym przykładzie pokazano, jak używać klasy pochodnej `Handles` instrukcję, aby obsłużyć zdarzenie z klasy bazowej.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera dwa programy obsługi zdarzeń przycisku dla **aplikacji WPF** projektu.  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest równoważny do poprzedniego przykładu. `eventlist` w `Handles` klauzula zawiera zdarzenia dla obu przycisków.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Zobacz także

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent, instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
