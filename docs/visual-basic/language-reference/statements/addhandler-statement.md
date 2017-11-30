---
title: "AddHandler — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords: AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a>AddHandler — Instrukcja
Kojarzy zdarzenie z obsługi zdarzeń w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Części  
 `event`  
 Nazwa zdarzenia do obsługi.  
  
 `eventhandler`  
 Nazwa procedury, która obsługuje zdarzenie.  
  
## <a name="remarks"></a>Uwagi  
 `AddHandler` i `RemoveHandler` instrukcje umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w czasie wykonywania programu.  
  
 Podpis `eventhandler` procedury muszą być zgodne podpisu zdarzenia `event`.  
  
 `Handles` — Słowo kluczowe i `AddHandler` instrukcji zarówno umożliwiają określenie określone procedury obsługi zdarzeń w szczególności, że istnieją różnice. `AddHandler` Instrukcji procedury łączy się z zdarzenia w czasie wykonywania. Użyj `Handles` — słowo kluczowe podczas definiowania procedury, aby określić, czy obsługuje ona określonego zdarzenia. Aby uzyskać więcej informacji, zobacz [obsługuje](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  W przypadku niestandardowych zdarzeń `AddHandler` instrukcja wywołuje zdarzenie `AddHandler` metody dostępu. Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [RemoveHandler — instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Uchwyty](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
