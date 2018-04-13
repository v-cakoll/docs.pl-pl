---
title: PrintForm — Składnik (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 890d5a3a3f9c3a737a59e17fef0d4ac0407e9924
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="printform-component-visual-basic"></a>PrintForm — Składnik (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umożliwia drukowanie obraz formularza systemu Windows w czasie wykonywania. Jego zachowanie zastępuje te `PrintForm` metody we wcześniejszych wersjach programu Visual Basic.  
  
 Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>Informacje o składniku PrintForm  
 Typowy scenariusz dla formularzy systemu Windows jest utworzenie formularza, który jest sformatowany w sposób przypominający formularza papieru lub raportu, a następnie do drukowania w formie obrazu. Chociaż można używać <xref:System.Drawing.Printing.PrintDocument> składnika w tym celu będzie wymagać dużej ilości kodu. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika umożliwia drukowanie formularza drukarki, okno podglądu wydruku lub pliku obrazu bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika znajduje się na **Visual Basic PowerPacks** karcie **przybornika**. Przeciągnięte w formularzu zostanie wyświetlona na pasku składnika małych obszarze dolnej krawędzi formularza. Po wybraniu składnika można ustawić właściwości, które definiują zachowania w **właściwości** okna. Wszystkie te właściwości można również ustawić w kodzie. Można również utworzyć wystąpienia <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika w kodzie bez dodawania składnika w czasie projektowania.  
  
 Podczas drukowania formularza, wszystkie elementy obszaru klienta formularza są drukowane. Dotyczy to również wszystkich kontrolek oraz wszelkich tekstu i grafiki rysowane na formularzu za pomocą metod grafiki. Domyślnie pasek tytułu formularza, pasków przewijania i obramowania nie są drukowane. Również domyślnie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika drukuje widoczną część formularza. Na przykład jeśli użytkownik zmieni rozmiar formularza w czasie wykonywania, tylko formanty i grafiki, które są widoczne są podane.  
  
 Drukarki domyślne używane przez <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika jest określana przez ustawienia Panelu sterowania systemu operacyjnego.  
  
 Po zainicjowaniu drukowanie standard <xref:System.Drawing.Printing.PrintDocument> zostanie wyświetlone okno dialogowe drukowania. To okno dialogowe umożliwia anulowanie zadania drukowania.  
  
### <a name="key-methods-properties-and-events"></a>Klucz metod, właściwości i zdarzeń  
 Metoda klucza <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik jest <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metodę, która wyświetla obraz formularza drukarki, okno podglądu wydruku lub pliku. Istnieją dwie wersje <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metody:  
  
-   Wersja podstawowa bez parametrów: `Print()`  
  
-   Przeciążone wersji z parametrami, które określają zachowanie drukowania: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     `PrintOption` Parametr przeciążonej metody określa implementacja używane do drukowania formularza, czy pasek tytułu formularza, pasków przewijania i obramowania są drukowane i czy są drukowane przewijanego części formularza.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Właściwość jest właściwością klucza <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika. Ta właściwość określa jest wysyłane do drukarki, wyświetlane w oknie Podgląd wydruku lub zapisany jako plik Encapsulated PostScript dane wyjściowe. Jeśli <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość jest ustawiona na <xref:System.Drawing.Printing.PrintAction.PrintToFile>, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> właściwość określa ścieżkę i nazwę pliku.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Właściwości zapewnia dostęp do podstawowej <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> obiekt, który umożliwia określenie ustawieniami, takimi jak drukarki i liczbę kopii do drukowania. Możesz także zbadać możliwości drukarki, takie jak kolor lub dupleks pomocy technicznej. Ta właściwość nie jest widoczna w **właściwości** okna; jest możliwy tylko z kodu.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Właściwość jest używana do określania formularza do drukowania po wywołaniu <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika programowo. Jeśli składnik zostanie dodany do formularza w czasie projektowania, formularz jest ustawieniem domyślnym.  
  
 Klucz zdarzenia <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika są następujące:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> zdarzenie. Występuje, gdy <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda jest wywoływana przed na pierwszej stronie drukuje dokument.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> zdarzenie. Występuje po wydrukowaniu ostatniej strony.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> zdarzenie. Występuje tuż przed wydrukowaniem każdej strony.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formularz zawiera tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metod, Użyj podstawowego <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) metodę, aby go wydrukować. Grafika może nie być wyświetlana w niektórych systemach operacyjnych gdy przeciążona <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda jest używana.  
  
 Jeśli szerokość formularza jest większa niż szerokość papieru w drukarce, z prawej strony formularza może zostać obcięta. Podczas projektowania formularzy do drukowania, upewnij się, odpowiadającego formularza na standardowych wymiarach papieru.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono użycie wspólnej <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika.  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [Instrukcje: drukowanie formularza za pomocą składnika PrintForm](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [Instrukcje: drukowanie obszarów klienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Instrukcje: drukowanie formularza przewijanego](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
