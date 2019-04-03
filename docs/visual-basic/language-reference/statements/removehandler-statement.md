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
ms.openlocfilehash: 8a9dc5874629c1687318496bd7c4016eb318c25a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831686"
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
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także

- [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
