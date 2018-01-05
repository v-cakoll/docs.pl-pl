---
title: "Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9aec07ab0f0897fcabcc2980dea5ef52d81082a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku
Jest bardzo często programowania oferowanie podglądu wydruku, oprócz usługi drukowania formularzy systemu Windows. Prosty sposób dodawania usługi podglądu wydruku do aplikacji jest użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontroli w połączeniu z <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiki obsługi zdarzeń do drukowania pliku.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Aby wyświetlić podgląd dokument tekstowy o printpreviewdialog — formant  
  
1.  Dodaj <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>i dwa ciągi do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwości dokumentu chcesz drukowania i otwierać i odczytywać zawartość dokumentu do ciągu dodane wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  Jak w przypadku drukowanie dokumentu, w <xref:System.Drawing.Printing.PrintDocument.PrintPage> program obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartość pliku do obliczania wierszy na stronie i renderowania zawartości dokumentu. Po każdej stronie jest, sprawdź, czy jest to ostatnia strona i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Zdarzenie jest wywoływane przed <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> jest `false`. Po zakończeniu renderowania dokumentu zresetować parametry do renderowania. Upewnij się również, <xref:System.Drawing.Printing.PrintDocument.PrintPage> wydarzenie jest skojarzone z metody obsługi zdarzeń.  
  
    > [!NOTE]
    >  Może zostały już wykonane kroki 2 i 3, jeśli zostały zaimplementowane drukowanie w aplikacji.  
  
     W poniższym przykładzie kodu programu obsługi zdarzeń służy do drukowania pliku "testPage.txt" w tej samej czcionki w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  Ustaw <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintPreviewDialog> formant <xref:System.Drawing.Printing.PrintDocument> składnika w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda <xref:System.Windows.Forms.PrintPreviewDialog> formantu. Zwykle możesz wywołać <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metoda obsługi zdarzeń przycisku. Wywoływanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> zgłasza <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń i renderuje dane wyjściowe do <xref:System.Windows.Forms.PrintPreviewDialog> formantu. Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest zgłaszane, wysyła dane wyjściowe do drukarki zamiast okna dialogowego podglądu. Jest to, dlaczego ten ciąg jest resetowany pod koniec procesu renderowania w kroku 3.  
  
     Poniższy kod przedstawia przykład <xref:System.Windows.Forms.Control.Click> metoda obsługi zdarzeń dla przycisku w formularzu. Ta metoda obsługi zdarzeń wywołuje metody służące do odczytu dokumentu i wyświetlenie okna dialogowego podglądu wydruku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do systemu, System.Windows.Forms, System.Drawing zestawów.  
  
-   Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Bezpieczniejsze drukowanie w formularzach Windows Forms](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
