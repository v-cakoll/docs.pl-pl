---
title: "&#39; Niestandardowe &#39; Modyfikator jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords: BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39; Niestandardowe &#39; Modyfikator jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
W przeciwieństwie do zdarzeń niestandardowych z systemem innym niż `Custom Event` deklaracja wymaga `As` klauzuli po nazwie zdarzenia, która jawnie określa typ delegata zdarzenia.  
  
 Zdarzenia niestandardowe nie może być zdefiniowany za pomocą `As` klauzuli i jawnych typ delegata lub z parametrem listy natychmiast po nazwie zdarzenia.  
  
 **Identyfikator błędu:** BC31122  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zdefiniuj delegata o tej samej listy parametrów jako zdarzenie niestandardowe.  
  
     Na przykład jeśli `Custom Event` został zdefiniowany przez `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, a następnie odpowiedniego delegata będą następujące.  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Zastąp parametr listę niestandardowych zdarzeń z `As` klauzuli Określanie typu obiektu delegowanego.  
  
     Przykładzie, `Custom Event` deklaracji będzie ponownie zapisać w następujący sposób.  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie deklaruje `Custom Event` i określa wymaganych `As` klauzuli z typem delegowanym.  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
