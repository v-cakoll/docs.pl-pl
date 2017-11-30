---
title: "RemoveHandler — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a>RemoveHandler — Instrukcja
Usuwa skojarzenie między zdarzeniem i program obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`event`|Nazwa zdarzenia, które są obsługiwane.|  
|`eventhandler`|Nazwa procedury obecnie obsługi zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 `AddHandler` i `RemoveHandler` instrukcje umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w czasie wykonywania programu.  
  
> [!NOTE]
>  W przypadku niestandardowych zdarzeń `RemoveHandler` instrukcja wywołuje zdarzenie `RemoveHandler` metody dostępu. Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Uchwyty](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
