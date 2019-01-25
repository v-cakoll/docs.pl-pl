---
title: '&#39;Niestandardowe&#39; modyfikator jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c909973ef1c00cb01179b0e5527dfecd6f41e577
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574784"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;Niestandardowe&#39; modyfikator jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
W przeciwieństwie do zdarzenia niestandardowe nie `Custom Event` deklaracja wymaga `As` klauzuli po nazwie zdarzeń, który jawnie określa typ delegata zdarzenia.  
  
 Zdarzenia niestandardowe nie mogą być zdefiniowane przy użyciu `As` klauzuli jawny typ delegata, a z parametrem listy natychmiast po nazwie zdarzeń.  
  
 **Identyfikator błędu:** BC31122  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zdefiniowanie pełnomocnika z tej samej listy parametrów jako zdarzenie niestandardowe.  
  
     Na przykład jeśli `Custom Event` został zdefiniowany przez `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, a następnie odpowiedniego delegata będą naliczane w następujący.  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Zastąp zdarzenie niestandardowe z listy parametrów `As` klauzuli określający typ delegata.  
  
     Kontynuując w przykładzie `Custom Event` deklaracja może zostać przepisane, w następujący sposób.  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie deklaruje `Custom Event` i określa wymagane `As` klauzuli z typem delegowanym.  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
