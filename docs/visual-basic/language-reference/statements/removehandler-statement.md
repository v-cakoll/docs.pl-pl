---
title: RemoveHandler — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: c1e6ffec64bc01936955a2e94aa9c110b317109f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925169"
---
# <a name="removehandler-statement"></a>RemoveHandler — Instrukcja
Usuwa skojarzenie między zdarzeniem, a program obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`event`|Nazwa przetwarzanego zdarzenia.|  
|`eventhandler`|Nazwa procedury obecnie obsługi zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 `AddHandler` i `RemoveHandler` instrukcje umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.  
  
> [!NOTE]
>  W przypadku zdarzeń niestandardowych instrukcja `RemoveHandler` wywołuje metodę dostępu zdarzenia `RemoveHandler`. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
