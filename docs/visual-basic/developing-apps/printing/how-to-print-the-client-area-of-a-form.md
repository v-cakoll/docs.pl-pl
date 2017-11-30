---
title: "Porady: drukowanie obszarów klienckich formularza (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42dd3c809ff0a1594350e252d4c4aa2f0ec004
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>Porady: drukowanie obszarów klienckich formularza (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie wydrukowanie obrazu formularza bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika. Poniższa procedura przedstawia sposób drukowanie tylko obszarów klienckich formularza, bez paska tytułu, obramowania i paski przewijania.  
  
 Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-client-area-of-a-form"></a>Drukowanie obszarów klienckich formularza  
  
1.  W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika jest dodawany do składnika na pasku zadań.  
  
2.  W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla **drukowania**`Button`).  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie mogą drukować poprawnie. W takim przypadku należy użyć metody drukowania zgodne:`PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Porady: drukowanie obszarów klienckich formularza i](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Porady: Drukowanie formularza przewijanego](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
