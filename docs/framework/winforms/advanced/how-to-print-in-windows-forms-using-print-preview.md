---
title: 'Instrukcje: Drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: d803c9bec180f45c80e362af49c8eaa12bb9d985
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592959"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Instrukcje: Drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku
Często zdarza się w formularzach Windows programowania do zaoferowania podglądu wydruku oprócz usług drukowania. Łatwe dodawanie usług podglądu wydruku do aplikacji jest użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontroli w połączeniu z <xref:System.Drawing.Printing.PrintDocument.PrintPage> logikę obsługi zdarzeń do drukowania pliku.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Aby wyświetlić podgląd dokument tekstowy o PrintPreviewDialog, kontrolka  
  
1. Dodaj <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, a dwa ciągi do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwości do dokumentu, które chcesz wydrukować i Otwórz, a odczytu zawartości dokumentu na ciąg zostanie dodane wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Podobnie jak w przypadku drukowanie dokumentu, w <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartość pliku do obliczania wierszy na stronie i renderują zawartość dokumentu. Po każdej stronie jest rysowana, sprawdź, czy jest ostatniej strony i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Zdarzenie jest zgłaszane do momentu <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> jest `false`. Po zakończeniu renderowania dokumentu zresetować parametry do renderowania. Upewnij się również, <xref:System.Drawing.Printing.PrintDocument.PrintPage> wydarzenie jest skojarzone z jego metody obsługi zdarzeń.  
  
    > [!NOTE]
    >  Może zostały już wykonane kroki 2 i 3, jeśli udało Ci się wdrożyć drukowanie w aplikacji.  
  
     W poniższym przykładzie kodu programu obsługi zdarzeń służy do drukowania pliku "testPage.txt" w tym samym czcionki używanej w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Ustaw <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintPreviewDialog> kontrolę <xref:System.Drawing.Printing.PrintDocument> składnika w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Wywołaj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody <xref:System.Windows.Forms.PrintPreviewDialog> kontroli. Zazwyczaj wywoływałby <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metody obsługi zdarzeń przycisku. Wywoływanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> zgłasza <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń i renderuje dane wyjściowe do <xref:System.Windows.Forms.PrintPreviewDialog> kontroli. Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest zgłaszane ponownie wysyła dane wyjściowe do drukarki zamiast okna dialogowego podglądu. Jest to, dlaczego ten ciąg jest resetowany po zakończeniu procesu renderowania w kroku 3.  
  
     Poniższy kod przedstawia przykład <xref:System.Windows.Forms.Control.Click> metody obsługi zdarzeń dla przycisku w formularzu. Ta metoda obsługi zdarzeń wywołuje metody służące do odczytu, Pokaż okno dialogowe podglądu wydruku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do systemu, przestrzeń nazw System.Windows.Forms, System.Drawing zestawów.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Podglądu wydruku w formularzach Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
- [Bezpieczniejsze drukowanie w formularzach Windows Forms](../more-secure-printing-in-windows-forms.md)
