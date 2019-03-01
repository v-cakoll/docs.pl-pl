---
title: Modyfikator „Custom” jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c50cee530cab0d5d164d930678651f302ddc7f09
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980766"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>Modyfikator „Custom” jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
W przeciwieństwie do zdarzenia niestandardowe nie `Custom Event` deklaracja wymaga `As` klauzuli po nazwie zdarzeń, który jawnie określa typ delegata zdarzenia.  
  
 Zdarzenia niestandardowe nie mogą być zdefiniowane przy użyciu `As` klauzuli jawny typ delegata, a z parametrem listy natychmiast po nazwie zdarzeń.  
  
 **Identyfikator błędu:** BC31122  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zdefiniowanie pełnomocnika z tej samej listy parametrów jako zdarzenie niestandardowe.  
  
     Na przykład jeśli `Custom Event` został zdefiniowany przez `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, a następnie odpowiedniego delegata będą naliczane w następujący.  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2.  Zastąp zdarzenie niestandardowe z listy parametrów `As` klauzuli określający typ delegata.  
  
     Kontynuując w przykładzie `Custom Event` deklaracja może zostać przepisane, w następujący sposób.  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie deklaruje `Custom Event` i określa wymagane `As` klauzuli z typem delegowanym.  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
