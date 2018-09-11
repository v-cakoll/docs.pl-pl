---
title: PrintForm — Składnik (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: 879d31c5a572689d84af6b2e46f3d33e1a8841c8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264301"
---
# <a name="printform-component-visual-basic"></a>PrintForm — Składnik (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika dla języka Visual Basic umożliwia drukowanie obraz formularza Windows w czasie wykonywania. Jego zachowanie zastąpi ten `PrintForm` metoda we wcześniejszych wersjach programu Visual Basic.  
  
 Kontrolki pakietu PowerPack nie są już dostępne w programie Visual Studio, ale można je pobrać w [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="printform-component-overview"></a>Printform — składnik — omówienie  
 Typowy scenariusz dla formularzy Windows Forms jest utworzenie formularz, który jest sformatowany w sposób przypominający formularza dokument lub raportu, a następnie do drukowania w formie obrazu. Chociaż można używać <xref:System.Drawing.Printing.PrintDocument> składnika, aby to zrobić, będzie to wymagać dużej ilości kodu. <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika umożliwia drukowanie obraz formularza do drukarki, do okna podglądu wydruku lub do pliku bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik znajduje się na **Visual Basic PowerPacks** karcie **przybornika**. Przeciągnięte na formularzu pojawi się w zasobniku składnika mały obszar, w obszarze dolną krawędź formularza. Po wybraniu składnika można ustawić właściwości, które definiują zachowanie w **właściwości** okna. Wszystkie te właściwości można również ustawić w kodzie. Można również utworzyć wystąpienie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika w kodzie bez dodawania składnika w czasie projektowania.  
  
 Podczas drukowania formularza, wszystkie elementy obszaru klienta formularza są drukowane. Dotyczy to wszystkich kontrolek i dowolny tekst lub grafiki rysowane na formularzu za pomocą metod grafiki. Domyślnie pasek tytułu, paski przewijania i obramowanie formularza nie są drukowane. Również domyślnie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika drukuje widoczne części formularza. Na przykład jeśli użytkownik zmienia rozmiar formularza, w czasie wykonywania, tylko formanty i grafiki, które są obecnie widoczne są drukowane.  
  
 Zostanie użyta drukarka domyślna używana przez <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika jest określana przez ustawienia Panelu sterowania systemu operacyjnego.  
  
 Po zainicjowaniu drukowanie standardowego <xref:System.Drawing.Printing.PrintDocument> zostanie wyświetlone okno dialogowe drukowania. To okno dialogowe umożliwia użytkownikom anulować zadanie drukowania.  
  
### <a name="key-methods-properties-and-events"></a>Klucz metody, właściwości i zdarzenia  
 Metoda klucza <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik to <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metody, która wyświetla obraz formularza do drukarki, okno podglądu wydruku lub pliku. Istnieją dwie wersje <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metody:  
  
-   Wersja podstawowa, bez parametrów: `Print()`  
  
-   Przeciążona wersja z parametrami, które określają zachowanie drukowania: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     `PrintOption` Parametr przeciążonej metody określa podstawowej implementacji, które są używane do drukowania w formularzu, czy pasek tytułu formularza, paski przewijania i obramowania są drukowane oraz tego, czy są drukowane przewijany części formularza.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> Właściwość jest właściwością klucza <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika. Ta właściwość określa jest wysyłane do drukarki, wyświetlane w oknie podglądu wydruku lub zapisany jako plik Encapsulated PostScript dane wyjściowe. Jeśli <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość jest ustawiona na <xref:System.Drawing.Printing.PrintAction.PrintToFile>, <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> właściwość określa ścieżkę i nazwę pliku.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> Właściwości zapewnia dostęp do bazowych <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> obiekt, który pozwala na określenie ustawieniami, takimi jak drukarki i liczbę kopii do wydrukowania. Możesz także zbadać możliwości drukarki, takie jak kolor lub dupleks pomocy technicznej. Ta właściwość nie jest widoczna w **właściwości** okna; jest możliwy tylko z kodu.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> Właściwość jest używana do określenia formularza do drukowania po wywołaniu <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika programowo. Jeśli ten składnik zostanie dodany do formularza w czasie projektowania, które tworzą jest ustawieniem domyślnym.  
  
 Klucz zdarzeń dla <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika obejmują następujące elementy:  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> zdarzenie. Występuje, gdy <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda jest wywoływana i przed pierwszą stronę spowoduje wydrukowanie dokumentu.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> zdarzenie. Występuje po ostatniej strony zostanie wydrukowany.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> zdarzenie. Występuje bezpośrednio przed wykonaniem każdej strony, wydrukowaniu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formularz zawiera tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody, za pomocą podstawowego <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) metodę, aby wydrukować. Grafika może nie być wyświetlana w niektórych systemach operacyjnych po przeciążone <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> metoda jest używana.  
  
 Jeśli szerokość formularza jest większa niż szerokość papieru drukarki, może być obcięty po prawej stronie formularza. Podczas projektowania formularzy do drukowania, upewnij się, odpowiadającego formularza na papierze o rozmiarze standard.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano typowym zastosowaniem <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika.  
  
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
