---
title: Handles, klauzula
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: df786e4b0f0ab3795592ea57f7af17695b086cfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404579"
---
# <a name="handles-clause-visual-basic"></a>Handles — Klauzula (Visual Basic)
Deklaruje, że procedura obsługuje określone zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>Części  
 `proceduredeclaration`  
 `Sub`Deklaracja procedury dla procedury, która będzie obsługiwać zdarzenie.  
  
 `eventlist`  
 Lista zdarzeń `proceduredeclaration` do obsługi, rozdzielonych przecinkami. Zdarzenia muszą być wywoływane przez klasę bazową dla bieżącej klasy lub przez obiekt zadeklarowany za pomocą `WithEvents` słowa kluczowego.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `Handles` słowa kluczowego na końcu deklaracji procedury, aby spowodować obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną za pomocą `WithEvents` słowa kluczowego. `Handles`Słowo kluczowe może być również używane w klasie pochodnej do obsługi zdarzeń z klasy bazowej.  
  
 `Handles`Słowo kluczowe i `AddHandler` instrukcja umożliwiają określenie, że konkretne procedury obsługują określone zdarzenia, ale istnieją różnice. Użyj `Handles` słowa kluczowego podczas definiowania procedury, aby określić, że obsługuje określone zdarzenie. `AddHandler`Instrukcja łączy procedury ze zdarzeniami w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [AddHandler instrukcji](addhandler-statement.md).  
  
 W przypadku zdarzeń niestandardowych aplikacja wywołuje metodę dostępu do zdarzenia, `AddHandler` gdy dodaje procedurę jako program obsługi zdarzeń. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 W poniższym przykładzie pokazano, jak Klasa pochodna może używać `Handles` instrukcji do obsługi zdarzenia z klasy bazowej.  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera dwa programy obsługi zdarzeń przycisków dla projektu **aplikacji WPF** .  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest równoważny z poprzednim przykładem. `eventlist` `Handles` Klauzula in zawiera zdarzenia dla obu przycisków.  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a>Zobacz też

- [WithEvents](../modifiers/withevents.md)
- [AddHandler — Instrukcja](addhandler-statement.md)
- [RemoveHandler — Instrukcja](removehandler-statement.md)
- [Event — Instrukcja](event-statement.md)
- [RaiseEvent — Instrukcja](raiseevent-statement.md)
- [Zdarzenia](../../programming-guide/language-features/events/index.md)
