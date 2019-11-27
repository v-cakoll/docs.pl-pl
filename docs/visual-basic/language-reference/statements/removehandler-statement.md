---
title: RemoveHandler — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 177952acf362ccb36a36b5f09b11a1a93dbefa29
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333038"
---
# <a name="removehandler-statement"></a>RemoveHandler — Instrukcja
Usuwa skojarzenie między zdarzeniem a programem obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`event`|Nazwa obsługiwanego zdarzenia.|  
|`eventhandler`|Nazwa procedury, która obecnie obsługuje zdarzenie.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.  
  
> [!NOTE]
> W przypadku zdarzeń niestandardowych instrukcja `RemoveHandler` wywołuje metodę dostępu `RemoveHandler` zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także

- [AddHandler, instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Realizuj](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
