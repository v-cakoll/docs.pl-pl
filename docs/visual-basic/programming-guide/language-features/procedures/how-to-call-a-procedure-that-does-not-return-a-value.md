---
title: 'Porady: wywoływanie procedury, która nie zwraca wartości'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3a5de98c6edf795a11bd9f0465aa6919f09eebfa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340958"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)
Procedura `Sub` nie zwraca wartości do kodu wywołującego. Należy wywołać ją jawnie z autonomiczną instrukcją wywołującą. Nie można go wywołać za pomocą jego nazwy w wyrażeniu.  
  
### <a name="to-call-a-sub-procedure"></a>Aby wywołać procedurę sub  
  
1. Określ nazwę procedury `Sub`.  
  
2. Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy. Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że podasz argumenty w tej samej kolejności, w której procedura `Sub` definiuje odpowiednie parametry.  
  
     Poniższy przykład wywołuje funkcję Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> w celu aktywowania okna aplikacji. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> przyjmuje jako jedyny argument tytułu okna. Nie zwraca wartości do kodu wywołującego. Jeśli proces Notatnika nie jest uruchomiony, przykład zgłosi <xref:System.ArgumentException>. W procedurze `Shell` przyjęto założenie, że aplikacje znajdują się w określonych ścieżkach.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrukcje: tworzenie procedury](./how-to-create-a-procedure.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
- [Instrukcje: wywoływanie procedury obsługi zdarzeń w Visual Basic](./how-to-call-an-event-handler.md)
