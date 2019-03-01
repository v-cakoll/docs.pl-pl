---
title: AddHandler — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: dd57f63b5741822de7b11c1fafe90452a767aa34
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965647"
---
# <a name="addhandler-statement"></a>AddHandler — Instrukcja
Kojarzy zdarzenie z programem obsługi zdarzeń w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Części  
|||
|---|---|
|zdarzenie|Nazwa zdarzenia do obsługi.|  
|`eventhandler`|Nazwa procedury, która obsługuje zdarzenie.|
|||
  
## <a name="remarks"></a>Uwagi  
 Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w dowolnym czasie podczas wykonywania programu.  
  
 Podpis procedury `eventhandler` musi być zgodny z podpisem zdarzenia `event`.  
  
 Zarówno słowo kluczowe `Handles`, jak i instrukcja `AddHandler` umożliwiają określenie konkretnych procedur do obsługi konkretnych zdarzeń, ale występują tu pewne różnice. Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania. Słowa kluczowego `Handles` należy użyć podczas definiowania procedury, aby określić, że ma ona obsługiwać konkretne zdarzenie. Aby uzyskać więcej informacji, zobacz artykuł [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
  
> [!NOTE]
>  W przypadku zdarzeń niestandardowych instrukcja `AddHandler` wywołuje metodę dostępu zdarzenia `AddHandler`. Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także
- [RemoveHandler, instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
