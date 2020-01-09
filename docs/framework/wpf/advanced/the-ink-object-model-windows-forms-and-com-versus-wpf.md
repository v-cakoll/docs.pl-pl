---
title: 'Model obiektu atramentowego: Windows Forms i COM, a WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
ms.openlocfilehash: 2c0d155d320bab2f0114280e962c8f2f0b559681
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636422"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Model obiektu atramentowego: Windows Forms i COM, a WPF

Istnieją głównie trzy platformy, które obsługują cyfrowy atrament: Windows Forms platformę, platformę COM komputera typu tablet i platformę Windows Presentation Foundation (WPF).  Platformy Windows Forms i COM współużytkują podobny model obiektów, ale model obiektów dla platformy WPF jest znacznie różny.  W tym temacie omówiono różnice na wysokim poziomie, dzięki czemu deweloperzy, którzy pracowały z jednym modelem obiektów, mogą lepiej zrozumieć inne.  
  
## <a name="enabling-ink-in-an-application"></a>Włączanie atramentu w aplikacji  
 Wszystkie trzy platformy dostarczają obiekty i kontrolki, które umożliwiają aplikacji odbieranie danych wejściowych z pióra rysownicy.  Windows Forms i platformy COM są dostarczane z klasami [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) i [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .  [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) i [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)) są kontrolkami, które można dodać do aplikacji w celu zbierania pisma odręcznego.  Elementy [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) i [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) można dołączać do istniejącego okna, aby umożliwić odpisanie atramentu i kontrolek niestandardowych.  
  
 Platforma WPF zawiera formant <xref:System.Windows.Controls.InkCanvas>.  Możesz dodać <xref:System.Windows.Controls.InkCanvas> do aplikacji i natychmiast rozpocząć zbieranie pisma odręcznego. Za pomocą <xref:System.Windows.Controls.InkCanvas>użytkownik może kopiować, wybierać i zmieniać rozmiar atramentu.  Możesz dodać inne kontrolki do <xref:System.Windows.Controls.InkCanvas>, a użytkownik może również ręcznie odpisać te formanty.  Można utworzyć kontrolkę niestandardową z obsługą atramentu, dodając do niej <xref:System.Windows.Controls.InkPresenter> i zbierając jej punkty pióra.  
  
 Poniższa tabela zawiera informacje o tym, gdzie można dowiedzieć się więcej na temat włączania atramentu w aplikacji:  
  
|Aby to zrobić...|Na platformie WPF...|Na platformach Windows Forms/COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Dodawanie kontrolki z obsługą atramentu do aplikacji|Zobacz [wprowadzenie z atramentem](getting-started-with-ink.md).|Zobacz [przykład Autooświadczenia formularza](/windows/desktop/tablet/auto-claims-form-sample)|  
|Włącz pismo odręczne na kontrolce niestandardowej|Zobacz [Tworzenie kontrolki wprowadzania atramentu](creating-an-ink-input-control.md).|Zobacz [przykład schowka odręcznego](/windows/desktop/tablet/ink-clipboard-sample).|  
  
## <a name="ink-data"></a>Dane odręczne  
 Na platformach Windows Forms i COM, [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkEdit](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))oraz [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) każdy uwidacznia obiekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) . Obiekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) zawiera dane dla jednego lub większej liczby obiektów [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) i udostępniają typowe metody i właściwości umożliwiające zarządzanie tymi pociągnięćmi i manipulowanie nimi.  Obiekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) zarządza okresem istnienia pociągnięć, które zawiera; Obiekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) tworzy i usuwa pociągnięcia, które posiada.  Każdy plik [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) ma identyfikator, który jest unikatowy w obrębie obiektu nadrzędnego [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) .  
  
 Na platformie WPF Klasa <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> jest właścicielem i zarządza własnym okresem istnienia. Grupę obiektów <xref:System.Windows.Ink.Stroke> można zbierać razem w <xref:System.Windows.Ink.StrokeCollection>, która zapewnia metody typowych operacji zarządzania danymi atramentowymi, takich jak testowanie trafień, wymazywanie, przekształcanie i Serializowanie atramentu. <xref:System.Windows.Ink.Stroke> może należeć do zero, jeden lub więcej obiektów <xref:System.Windows.Ink.StrokeCollection> w dowolnym momencie.  Zamiast mieć obiekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) , <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter> zawierają <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Poniższa para ilustracji porównuje modele obiektów danych atramentu.  Na platformach Windows Forms i COM obiekt [Microsoft. Ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) ogranicza okres istnienia obiektów [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) , a pakiety pióra należą do poszczególnych pociągnięć.  Co najmniej dwa pociągnięcia mogą odwoływać się do tego samego obiektu [Microsoft. Ink. DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90)) , jak pokazano na poniższej ilustracji.  
  
 ![Diagram modelu obiektów Ink dla kontrolek typu&#47;com.](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]każdy <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> jest obiektem środowiska uruchomieniowego języka wspólnego, który istnieje, o ile ma odwołanie do niego.  Każdy <xref:System.Windows.Ink.Stroke> odwołuje się do obiektu <xref:System.Windows.Input.StylusPointCollection> i <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType>, które są również obiektami środowiska uruchomieniowego języka wspólnego.  
  
 ![Diagram modelu obiektów Ink dla WPF.](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 W poniższej tabeli porównano, jak wykonać typowe zadania na platformie WPF i Windows Forms i platformie COM.  
  
|Zadanie|Windows Presentation Foundation|Windows Forms i COM|  
|----------|-------------------------------------|---------------------------|  
|Zapisz atrament|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|Ładowanie atramentu|Utwórz <xref:System.Windows.Ink.StrokeCollection> za pomocą konstruktora <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A>.|[Microsoft.Ink.Ink.Load](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|Test trafień|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|Kopiuj atrament|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|Wklej atrament|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|Dostęp do właściwości niestandardowych w kolekcji pociągnięć|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (właściwości są przechowywane wewnętrznie i dostępne za pośrednictwem <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>i <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>).|Użyj [Microsoft. Ink. Ink. Właściwości ExtendedProperties](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90))|  
  
### <a name="sharing-ink-between-platforms"></a>Udostępnianie farby między platformami  
 Chociaż platformy mają różne modele obiektów dla danych farb, udostępnianie danych między platformami jest bardzo proste. Poniższe przykłady zapisują atrament z aplikacji Windows Forms i ładowania atramentu do aplikacji Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Poniższe przykłady zapisują atrament z aplikacji Windows Presentation Foundation i ładowania atramentu do aplikacji Windows Forms.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Zdarzenia z pióra rysownicy  

 Elementy [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))i [Microsoft. ink. INKPICTURE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) na platformach Windows Forms i com odbierają zdarzenia, gdy użytkownik wprowadza dane pióra. Elementy [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) lub [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) są dołączone do okna lub kontrolki i mogą subskrybować zdarzenia wywoływane przez dane wejściowe tabletu. Wątek, w którym są wykonywane te zdarzenia, zależy od tego, czy zdarzenia są wywoływane za pomocą pióra, myszy, czy programowo. Aby uzyskać więcej informacji o wątkach w odniesieniu do tych zdarzeń, zobacz [ogólne kwestie wątkowe](/windows/desktop/tablet/general-threading-considerations) i [wątki, na których można uruchomić zdarzenie](/windows/desktop/tablet/threads-on-which-an-event-can-fire).  
  
 Na platformie Windows Presentation Foundation Klasa <xref:System.Windows.UIElement> ma zdarzenia dla danych wejściowych pióra. Oznacza to, że każdy formant uwidacznia pełen zestaw zdarzeń pióra.  Zdarzenia pióra mają pary zdarzeń tunelowania/propagacji i zawsze występują w wątku aplikacji.  Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 Na poniższym diagramie przedstawiono porównanie modeli obiektów dla klas, które powodują wywoływanie zdarzeń pióra. Windows Presentation Foundation model obiektów pokazuje tylko zdarzenia propagacji, a nie odpowiednie dla nich odpowiedniki zdarzeń tunelowania.  
  
 ![Diagram zdarzeń pióra w programie WPF a WinForms.](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Dane pióra  
 Wszystkie trzy platformy zapewniają sposoby przechwycenia i manipulowania danymi, które pochodzą z pióra rysownicy.  Na platformach Windows Forms i COM uzyskuje się to przez utworzenie obiektu [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)), dołączenie okna lub kontrolki do niego oraz utworzenie klasy implementującej interfejs [Microsoft. StylusInput. IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90)) lub [Microsoft. StylusInput. IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90)) . Niestandardowa wtyczka jest następnie dodawana do kolekcji wtyczek [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)). Aby uzyskać więcej informacji na temat tego modelu obiektów, zobacz [architektury interfejsów API StylusInput](/windows/desktop/tablet/architecture-of-the-stylusinput-apis).  
  
 Na platformie WPF Klasa <xref:System.Windows.UIElement> uwidacznia kolekcję wtyczek, podobnie jak w projekcie do [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90)).  Aby przechwycić dane pióra, Utwórz klasę, która dziedziczy po <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i Dodaj obiekt do kolekcji <xref:System.Windows.UIElement.StylusPlugIns%2A> <xref:System.Windows.UIElement>. Aby uzyskać więcej informacji na temat tej interakcji, zobacz [przechwytywanie danych wejściowych z pióra](intercepting-input-from-the-stylus.md).  
  
 Na wszystkich platformach Pula wątków otrzymuje dane odręczne za pośrednictwem zdarzeń pióra i wysyła je do wątku aplikacji.  Aby uzyskać więcej informacji o wątkach na platformach COM i Windows, zobacz [zagadnienia dotyczące wątkowości dla interfejsów API StylusInput](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis).  Aby uzyskać więcej informacji o wątkach oprogramowania prezentacji systemu Windows, zobacz [model wątkowości pisma odręcznego](the-ink-threading-model.md).  
  
 Poniższa ilustracja zawiera porównanie modeli obiektów dla klas, które odbierają dane pióra w puli wątków pióra.  
  
 ![Diagram modelu StylusPlugin WPF a WinForms.](./media/ink-stylusplugins.png "Ink_StylusPlugins")
