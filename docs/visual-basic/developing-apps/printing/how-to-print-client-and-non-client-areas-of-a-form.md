---
title: 'Porady: drukowanie obszarów klienckich i nieklienckich formularza (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408442"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a>Porady: drukowanie obszarów klienckich i nieklienckich formularza (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie drukowanie obraz formularza, dokładnie tak, jak wygląda na to, na ekranie bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika. Poniższa procedura pokazuje, jak drukowanie formularza, w tym obszar klienta i obszaru nieklienckiego. Obszaru nieklienckiego zawiera pasek tytułu, obramowania i przewijania pasków.  
  
 Formantów PowerPack znajdują się już w programie Visual Studio, ale można je pobrać [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a>Aby wydrukować zarówno klient, jak i obszarów klienckich formularza  
  
1.  W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** kartę, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika do formularza.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do zasobnika składnika.  
  
2.  W **właściwości** oknie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Dodaj następujący kod w obsłudze odpowiedniego zdarzenia (na przykład w `Click` program obsługi zdarzeń dla drukowania `Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie może poprawnie wydrukować. In this case, użyj kompatybilna metoda drukowania: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Instrukcje: drukowanie formularza przewijanego](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
