---
title: Drukuj przy użyciu podglądu wydruku
description: Dowiedz się, jak dodać usługi podglądu wydruku do aplikacji przy użyciu kontrolki PrintPreviewDialog Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621616"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku
Jest to bardzo popularne w Windows Forms programowaniu w celu oferowania podglądu wydruku oprócz usług drukowania. Łatwym sposobem dodawania usług podglądu wydruku do aplikacji jest użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki w połączeniu z <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiką obsługi zdarzeń do drukowania pliku.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Aby wyświetlić podgląd dokumentu tekstowego z kontrolką PrintPreviewDialog  
  
1. Dodaj <xref:System.Windows.Forms.PrintPreviewDialog> , <xref:System.Drawing.Printing.PrintDocument> i dwa ciągi do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> Właściwość na dokument, który chcesz wydrukować, i Otwórz i Odczytaj zawartość dokumentu do ciągu, który został dodany wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Podobnie jak w przypadku drukowania dokumentu, w programie <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń należy użyć <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwości <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartości pliku, aby obliczyć linie na stronie i renderować zawartość dokumentu. Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną, i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> Właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. <xref:System.Drawing.Printing.PrintDocument.PrintPage>Zdarzenie jest zgłaszane do momentu <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false` . Po zakończeniu renderowania dokumentu Zresetuj ciąg, który ma być renderowany. Upewnij się również, że <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest skojarzone z jego metodą obsługi zdarzeń.  
  
    > [!NOTE]
    > W przypadku zaimplementowania drukowania w aplikacji mogły już zostać wykonane kroki 2 i 3.  
  
     W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania pliku "testPage.txt" w tej samej czcionce, która jest używana w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Ustaw <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Właściwość <xref:System.Windows.Forms.PrintPreviewDialog> formantu na <xref:System.Drawing.Printing.PrintDocument> składnik w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Wywołaj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w <xref:System.Windows.Forms.PrintPreviewDialog> kontrolce. Zwykle jest wywoływana <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metody obsługi zdarzeń przycisku. Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> wywołuje <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie i renderuje dane wyjściowe do <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki. Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym, <xref:System.Drawing.Printing.PrintDocument.PrintPage> zostanie ponownie wywołane zdarzenie, wysyłając dane wyjściowe do drukarki zamiast okna dialogowego podglądu. To dlatego, że ciąg jest resetowany na końcu procesu renderowania w kroku 3.  
  
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

- [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Obsługa drukowania w formularzach systemu Windows](windows-forms-print-support.md)
- [Bezpieczniejsze drukowanie w formularzach systemu Windows](../more-secure-printing-in-windows-forms.md)
