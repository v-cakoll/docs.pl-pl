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
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404255"
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
 `AddHandler`Instrukcje i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.  
  
> [!NOTE]
> W przypadku zdarzeń niestandardowych `RemoveHandler` instrukcja wywołuje `RemoveHandler` metodę dostępu zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz też

- [AddHandler — Instrukcja](addhandler-statement.md)
- [Handles](handles-clause.md)
- [Event — Instrukcja](event-statement.md)
- [Zdarzenia](../../programming-guide/language-features/events/index.md)
