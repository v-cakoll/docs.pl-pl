---
title: 'Porady: drukowanie formularza za pomocą składnika PrintForm (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 723524c7c9876d353624ad47d504ea2528a31cfe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422730"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>Porady: drukowanie formularza za pomocą składnika PrintForm (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie drukowanie obraz formularza, dokładnie tak, jak wygląda na to, na ekranie bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika. Poniższe procedury pokazują, jak drukowanie formularza drukarki, okno podglądu wydruku i plik Encapsulated PostScript.  
  
 Formantów PowerPack znajdują się już w programie Visual Studio, ale można je pobrać [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-a-form-to-the-default-printer"></a>Aby wydrukować formularza zostanie użyta drukarka domyślna  
  
1.  W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** kartę, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika do formularza.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do zasobnika składnika.  
  
2.  W **właściwości** oknie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.  
  
3.  Dodaj następujący kod w obsłudze odpowiedniego zdarzenia (na przykład w `Click` program obsługi zdarzeń dla **drukowania**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>Aby wyświetlić formularz w oknie podglądu wydruku  
  
1.  W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** kartę, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika do formularza.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do zasobnika składnika.  
  
2.  W **właściwości** oknie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.  
  
3.  Dodaj następujący kod w obsłudze odpowiedniego zdarzenia (na przykład w `Click` program obsługi zdarzeń dla **drukowania**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>Aby wydrukować formularza do pliku  
  
1.  W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** kartę, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika do formularza.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do zasobnika składnika.  
  
2.  W **właściwości** oknie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość <xref:System.Drawing.Printing.PrintAction.PrintToFile>.  
  
3.  Opcjonalnie można zaznaczyć <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> właściwości i wpisz pełną ścieżkę i nazwę dla pliku docelowego.  
  
     Jeśli pominiesz ten krok, użytkownik jest monitowany o podanie nazwy pliku w czasie wykonywania.  
  
4.  Dodaj następujący kod w obsłudze odpowiedniego zdarzenia (na przykład w `Click` program obsługi zdarzeń dla **drukowania**`Button`).  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [Instrukcje: drukowanie obszarów klienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Instrukcje: drukowanie formularza przewijanego](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
