---
title: 'Instrukcje: Wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows'
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
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931790"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Instrukcje: Wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows
Drukowanie tekstu jest bardzo popularne dla aplikacji opartych na systemie Windows. <xref:System.Drawing.Graphics> Klasa zawiera metody rysowania obiektów (grafiki lub tekstu) na urządzeniu, takie jak ekran lub drukarka.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metodyniesą<xref:System.Windows.Forms.TextRenderer> obsługiwane na potrzeby drukowania. Należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics>metod, jak pokazano w poniższym przykładzie kodu, aby narysować tekst do celów drukowania.  
  
### <a name="to-print-text"></a>Aby wydrukować tekst  
  
1. <xref:System.Drawing.Printing.PrintDocument> Dodaj składnik i ciąg do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. W przypadku drukowania dokumentu Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwość na dokument, który chcesz wydrukować, a następnie otwórz i Odczytaj zawartość dokumentów do ciągu, który został dodany wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. W programie obsługi <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń Użyj właściwości klasy i zawartości dokumentu, aby obliczyć długość wiersza i wiersze na stronie. Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną, i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> Właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio. Zdarzenie jest <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> zgłaszane`false`domomentu. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Upewnij się również, że <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest skojarzone z jego metodą obsługi zdarzeń.  
  
     W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania zawartości pliku "testPage. txt" w tej samej czcionce jak w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Wywołaj <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby <xref:System.Drawing.Printing.PrintDocument.PrintPage> zgłosić zdarzenie.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Plik tekstowy o nazwie testPage. txt zawierający tekst do wydrukowania znajdujący się w katalogu głównym dysku C:\\. Edytuj kod, aby wydrukować inny plik.  
  
- Odwołania do zestawów system, system. Windows. Forms, system. Drawing.  
  
- Aby uzyskać informacje na temat tworzenia tego przykładu z wiersza polecenia dla Visual Basic C#lub wizualizacji, zobacz [Kompilowanie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [Kompilowanie wiersza polecenia za pomocą pliku CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Możesz również utworzyć ten przykład w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Obsługa drukowania w formularzach Windows Forms](windows-forms-print-support.md)
