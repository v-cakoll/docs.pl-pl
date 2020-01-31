---
title: Drukuj przy użyciu podglądu wydruku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 1975c902fdb56326c763f2e2fc11e381ffc7fbd3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740606"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku
Jest to bardzo popularne w Windows Forms programowaniu w celu oferowania podglądu wydruku oprócz usług drukowania. Łatwym sposobem dodawania usług podglądu wydruku do aplikacji jest użycie kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> w połączeniu z logiką obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> do drukowania pliku.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Aby wyświetlić podgląd dokumentu tekstowego z kontrolką PrintPreviewDialog  
  
1. Dodaj <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>i dwa ciągi do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Ustaw właściwość <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, który chcesz wydrukować, a następnie otwórz i Odczytaj zawartość dokumentu do ciągu, który został dodany wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Tak jak w przypadku drukowania dokumentu, w programie obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> Użyj właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs> i zawartości pliku, aby obliczyć linie na stronie i renderować zawartość dokumentu. Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną i odpowiednio ustaw właściwość <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs>. Zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest zgłaszane do momentu `false`<xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>. Po zakończeniu renderowania dokumentu Zresetuj ciąg, który ma być renderowany. Upewnij się również, że zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest skojarzone z jego metodą obsługi zdarzeń.  
  
    > [!NOTE]
    > W przypadku zaimplementowania drukowania w aplikacji mogły już zostać wykonane kroki 2 i 3.  
  
     W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania pliku "testPage. txt" w tej samej czcionce, która jest używana w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Ustaw właściwość <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> na składnik <xref:System.Drawing.Printing.PrintDocument> w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Wywołaj metodę <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> na kontrolce <xref:System.Windows.Forms.PrintPreviewDialog>. Zazwyczaj należy wywołać <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z metody obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> przycisku. Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> wywołuje zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> i renderuje dane wyjściowe do kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>. Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym, zostanie ponownie wywołane zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage>, wysyłając dane wyjściowe do drukarki zamiast okna dialogowego podglądu. To dlatego, że ciąg jest resetowany na końcu procesu renderowania w kroku 3.  
  
     Poniższy przykład kodu przedstawia metodę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku w formularzu. Ta metoda obsługi zdarzeń wywołuje metody odczytywania dokumentu i wyświetlania okna dialogowego podglądu wydruku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Windows. Forms, system. Drawing.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
- [Bezpieczniejsze drukowanie w formularzach Windows Forms](../more-secure-printing-in-windows-forms.md)
