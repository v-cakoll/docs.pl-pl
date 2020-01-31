---
title: 'Instrukcje: Drukowanie wielostronicowego pliku tekstowego'
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
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740661"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Porady: wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows
Drukowanie tekstu jest bardzo popularne dla aplikacji opartych na systemie Windows. Klasa <xref:System.Drawing.Graphics> zapewnia metody rysowania obiektów (grafiki lub tekstu) na urządzeniu, takie jak ekran lub drukarka.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metod <xref:System.Windows.Forms.TextRenderer> nie są obsługiwane na potrzeby drukowania. Należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metod <xref:System.Drawing.Graphics>, jak pokazano w poniższym przykładzie kodu, aby narysować tekst do celów drukowania.  
  
### <a name="to-print-text"></a>Aby wydrukować tekst  
  
1. Dodaj składnik <xref:System.Drawing.Printing.PrintDocument> i ciąg do formularza.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. W przypadku drukowania dokumentu ustaw właściwość <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, który chcesz wydrukować, a następnie otwórz i Odczytaj zawartość dokumentów do ciągu, który został dodany wcześniej.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. W obsłudze zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> Użyj właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs> i zawartości dokumentu, aby obliczyć długość i wiersze wierszy na stronie. Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną i odpowiednio ustaw właściwość <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs>. Zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest zgłaszane do momentu `false`<xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>. Upewnij się również, że zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest skojarzone z jego metodą obsługi zdarzeń.  
  
     W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania zawartości pliku "testPage. txt" w tej samej czcionce jak w formularzu.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Wywołaj metodę <xref:System.Drawing.Printing.PrintDocument.Print%2A>, aby zgłosić zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
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
