---
title: 'Porady: drukowanie formularza przewijanego (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: d43c2e0e564f6f0c37831cd3105a16c4bc4aaea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584017"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a>Porady: drukowanie formularza przewijanego (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie wydrukowanie obrazu formularza bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika. Domyślnie tylko widoczne części formularza jest drukowany; Jeśli użytkownik został zmieniony formularza w czasie wykonywania, obrazu nie mogą drukować, zgodnie z założeniami. Poniższa procedura przedstawia sposób Drukowanie obszarów klienckich pełne formularza przewijanego, nawet wtedy, gdy formularz został zmieniony.  
  
 Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a>Drukowanie obszarów klienckich pełne formularza przewijanego  
  
1.  W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do składnika na pasku zadań.  
  
2.  W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla **drukowania**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie mogą drukować poprawnie. W takim przypadku nie będzie możliwe do drukowania z `Scrollable` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Instrukcje: drukowanie obszarów klienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
