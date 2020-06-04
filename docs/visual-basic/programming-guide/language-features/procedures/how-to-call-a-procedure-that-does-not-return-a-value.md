---
title: 'Porady: wywoływanie procedury, która nie zwraca wartości'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 514d6e576b9b782387840ae04dcefa00de876aa9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388741"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)
`Sub`Procedura nie zwraca wartości do kodu wywołującego. Należy wywołać ją jawnie z autonomiczną instrukcją wywołującą. Nie można go wywołać za pomocą jego nazwy w wyrażeniu.  
  
### <a name="to-call-a-sub-procedure"></a>Aby wywołać procedurę sub  
  
1. Określ nazwę `Sub` procedury.  
  
2. Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy. Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że podasz argumenty w tej samej kolejności, w której `Sub` procedura definiuje odpowiednie parametry.  
  
     Poniższy przykład wywołuje <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkcję Visual Basic w celu aktywowania okna aplikacji. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>przyjmuje tytuł okna jako jedyny argument. Nie zwraca wartości do kodu wywołującego. Jeśli proces Notatnika nie jest uruchomiony, przykład zgłasza <xref:System.ArgumentException> . W `Shell` procedurze przyjęto założenie, że aplikacje znajdują się w określonych ścieżkach.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Sub, instrukcja](../../../language-reference/statements/sub-statement.md)
- [Porady: tworzenie procedury](./how-to-create-a-procedure.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
- [Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic](./how-to-call-an-event-handler.md)
