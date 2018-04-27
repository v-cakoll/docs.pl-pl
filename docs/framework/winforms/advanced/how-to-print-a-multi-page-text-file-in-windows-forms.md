---
title: 'Porady: wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd08d40c9b4e5f796c200966482781dfb2e700d8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Porady: wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows
Jest bardzo często dla aplikacji systemu Windows wydrukować tekst. <xref:System.Drawing.Graphics> Klasa zawiera metody służące do rysowania obiektów (grafiki lub tekst) na urządzeniu, na przykład ekranu lub drukarki.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> nie są obsługiwane na potrzeby drukowania. Zawsze należy używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak pokazano w poniższym przykładzie kodu ma zostać narysowany tekst do celów drukowania.  
  
### <a name="to-print-text"></a>Drukowanie tekstu  
  
1.  Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika i ciąg do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  Jeśli drukowanie dokumentu, ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwości dokumentu chcesz drukowania i otwierać i odczytywać zawartość dokumentów na ciąg dodane wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  W <xref:System.Drawing.Printing.PrintDocument.PrintPage> program obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartość dokumentu w celu obliczania długości i wierszy na stronie linii. Po każdej stronie jest, sprawdź, czy jest to ostatnia strona i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Zdarzenie jest wywoływane przed <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> jest `false`. Upewnij się również, <xref:System.Drawing.Printing.PrintDocument.PrintPage> wydarzenie jest skojarzone z metody obsługi zdarzeń.  
  
     W poniższym przykładzie kodu programu obsługi zdarzeń służy do drukowania zawartości pliku "testPage.txt" w tej samej czcionki, które jest używane w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  Wywołanie <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby podnieść <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Plik tekstowy o nazwie testPage.txt zawierającej tekst, aby wydrukować, znajduje się w folderze głównym dysku C:\\. Edytuj kod, aby wydrukować inny plik.  
  
-   Odwołania do systemu, System.Windows.Forms, System.Drawing zestawów.  
  
-   Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
