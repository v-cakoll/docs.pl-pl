---
title: AddHandler — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350190"
---
# <a name="addhandler-statement"></a>AddHandler — Instrukcja
Kojarzy zdarzenie z programem obsługi zdarzeń w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Części  
|||
|---|---|
|zdarzenie|Nazwa zdarzenia do obsłużenia.|  
|`eventhandler`|Nazwa procedury, która obsługuje zdarzenie.|
|||
  
## <a name="remarks"></a>Uwagi  
 Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w dowolnym momencie podczas wykonywania programu.  
  
 Sygnatura procedury `eventhandler` musi być zgodna z sygnaturą `event`zdarzenia.  
  
 Słowo kluczowe `Handles` i instrukcja `AddHandler` umożliwiają określenie, że konkretne procedury obsługują określone zdarzenia, ale istnieją różnice. Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania. Użyj słowa kluczowego `Handles` podczas definiowania procedury, aby określić, że obsługuje określone zdarzenie. Aby uzyskać więcej informacji, zobacz [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> W przypadku zdarzeń niestandardowych instrukcja `AddHandler` wywołuje metodę dostępu `AddHandler` zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także

- [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Realizuj](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
