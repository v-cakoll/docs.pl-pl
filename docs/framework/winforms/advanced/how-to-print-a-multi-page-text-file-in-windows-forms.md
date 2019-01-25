---
title: 'Instrukcje: Podglądu wydruku w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 149f0ca6df60931f8bb567ef5e4876c779825f1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604378"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Instrukcje: Podglądu wydruku w formularzach Windows Forms
Jest to często stosowane w aplikacjach Windows do drukowania tekstu. <xref:System.Drawing.Graphics> Klasa dostarcza metody do rysowania obiektów (grafiki lub tekst) do urządzenia, takich jak ekranu lub drukarki.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> nie są obsługiwane na potrzeby drukowania. Należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak pokazano w poniższym przykładzie kodu, aby rysować tekst na potrzeby drukowania.  
  
### <a name="to-print-text"></a>Aby wydrukować tekst  
  
1.  Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika i ciąg do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  Jeśli drukowanie dokumentu, ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwości dokumentu chcesz wydrukować i otwierać i odczytywać zawartość dokumentów, aby ten ciąg zostanie dodane wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  W <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartość dokumentu, aby obliczyć długość i wierszy na stronie linii. Po każdej stronie jest rysowana, sprawdź, czy jest ostatniej strony i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Zdarzenie jest zgłaszane do momentu <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> jest `false`. Upewnij się również, <xref:System.Drawing.Printing.PrintDocument.PrintPage> wydarzenie jest skojarzone z jego metody obsługi zdarzeń.  
  
     W poniższym przykładzie kodu programu obsługi zdarzeń służy do drukowania zawartości pliku "testPage.txt" w tej samej czcionki, ponieważ jest używany w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  Wywołaj <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby podnieść <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Plik tekstowy o nazwie testPage.txt zawierający tekst, aby wydrukować, znajduje się w folderze głównym dysku C:\\. Edytuj kod, aby wydrukować inny plik.  
  
-   Odwołania do systemu, przestrzeń nazw System.Windows.Forms, System.Drawing zestawów.  
  
-   Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
