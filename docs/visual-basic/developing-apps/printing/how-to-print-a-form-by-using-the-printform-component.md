---
title: 'Instrukcje: Drukowanie formularza za pomocą składnika PrintForm (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 0a1a62627390c8839625862b9d43d61fc07ebf12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521572"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>Instrukcje: Drukowanie formularza za pomocą składnika PrintForm (Visual Basic)
Składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> pozwala na szybkie wydrukowanie obrazu formularza, dokładnie tak, jak wygląda on na ekranie, bez użycia składnika <xref:System.Drawing.Printing.PrintDocument>. Poniższe procedury pokazują, jak drukować formularz na drukarce, w oknie podglądu wydruku i do pliku Encapsulated PostScript.   
  
 Kontrolki pakietu PowerPack nie są już dostępne w programie Visual Studio, ale można je pobrać w [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-a-form-to-the-default-printer"></a>Drukowanie formularza przy użyciu drukarki domyślnej  
  
1.  W **Przyborniku** kliknij kartę **Visual Basic PowerPacks**, a następnie przeciągnij składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> na formularz.   
  
     Składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> jest dodawany do zasobnika składników.   
  
2.  W oknie **Właściwości** ustaw właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> na <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.   
  
3.  Dodaj następujący kod do odpowiedniej procedury obsługi zdarzeń (na przykład obsługa zdarzenia `Click` dla przycisku (`Button`) **Drukuj**).   
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>Wyświetlanie formularza w oknie Podgląd wydruku  
  
1.  W **Przyborniku** kliknij kartę **Visual Basic PowerPacks**, a następnie przeciągnij składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> na formularz.   
  
     Składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> jest dodawany do zasobnika składników.   
  
2.  W oknie **Właściwości** ustaw właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> na <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.   
  
3.  Dodaj następujący kod do odpowiedniej procedury obsługi zdarzeń (na przykład obsługa zdarzenia `Click` dla przycisku (`Button`) **Drukuj**).   
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>Aby wydrukować formularza do pliku  
  
1.  W **Przyborniku** kliknij kartę **Visual Basic PowerPacks**, a następnie przeciągnij składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> na formularz.   
  
     Składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> jest dodawany do zasobnika składników.   
  
2.  W oknie **Właściwości** ustaw właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> na <xref:System.Drawing.Printing.PrintAction.PrintToFile>.   
  
3.   Opcjonalnie wybierz właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> i wpisz pełną ścieżkę oraz nazwę pliku dla pliku docelowego.  
  
     Jeśli pominiesz ten krok, użytkownik jest monitowany o podanie nazwy pliku w czasie wykonywania.  
  
4.  Dodaj następujący kod do odpowiedniej procedury obsługi zdarzeń (na przykład obsługa zdarzenia `Click` dla przycisku (`Button`) **Drukuj**).   
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>
- [Instrukcje: drukowanie obszarów klienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)
- [Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [Instrukcje: drukowanie formularza przewijanego](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
- [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
