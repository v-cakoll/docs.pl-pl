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
ms.openlocfilehash: 07137d03dd9a20d8eab564757618e48e25b45353
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931767"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Instrukcje: Drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku
Jest to bardzo popularne w Windows Forms programowaniu w celu oferowania podglądu wydruku oprócz usług drukowania. Łatwym sposobem dodawania usług podglądu wydruku do aplikacji jest użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki w połączeniu <xref:System.Drawing.Printing.PrintDocument.PrintPage> z logiką obsługi zdarzeń do drukowania pliku.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Aby wyświetlić podgląd dokumentu tekstowego z kontrolką PrintPreviewDialog  
  
1. <xref:System.Windows.Forms.PrintPreviewDialog>Dodaj, <xref:System.Drawing.Printing.PrintDocument>i dwa ciągi do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> Ustaw właściwość na dokument, który chcesz wydrukować, i Otwórz i Odczytaj zawartość dokumentu do ciągu, który został dodany wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Podobnie jak w przypadku drukowania dokumentu, w programie <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń należy <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> użyć właściwości <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartości pliku, aby obliczyć linie na stronie i renderować zawartość dokumentu. Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną, i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> Właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. Zdarzenie jest <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> zgłaszane`false`domomentu. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Po zakończeniu renderowania dokumentu Zresetuj ciąg, który ma być renderowany. Upewnij się również, że <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest skojarzone z jego metodą obsługi zdarzeń.  
  
    > [!NOTE]
    > W przypadku zaimplementowania drukowania w aplikacji mogły już zostać wykonane kroki 2 i 3.  
  
     W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania pliku "testPage. txt" w tej samej czcionce, która jest używana w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Ustaw właściwość <xref:System.Windows.Forms.PrintPreviewDialog> formantu na<xref:System.Drawing.Printing.PrintDocument> składnik w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Wywołaj <xref:System.Windows.Forms.PrintPreviewDialog> metodę w kontrolce. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Zwykle jest wywoływana <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> <xref:System.Windows.Forms.Control.Click> z metody obsługi zdarzeń przycisku. Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> wywołuje<xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie i<xref:System.Windows.Forms.PrintPreviewDialog> renderuje dane wyjściowe do kontrolki. Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym, <xref:System.Drawing.Printing.PrintDocument.PrintPage> zostanie ponownie wywołane zdarzenie, wysyłając dane wyjściowe do drukarki zamiast okna dialogowego podglądu. To dlatego, że ciąg jest resetowany na końcu procesu renderowania w kroku 3.  
  
     Poniższy przykład kodu pokazuje <xref:System.Windows.Forms.Control.Click> metodę obsługi zdarzeń dla przycisku w formularzu. Ta metoda obsługi zdarzeń wywołuje metody odczytywania dokumentu i wyświetlania okna dialogowego podglądu wydruku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Windows. Forms, system. Drawing.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Drukowanie wielostronicowego pliku tekstowego w Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
- [Bezpieczniejsze drukowanie w formularzach Windows Forms](../more-secure-printing-in-windows-forms.md)
