---
title: 'Model obiektu atramentowego: Windows Forms i COM, a WPF'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38c7692d433fb91584718984ef2ad81e563517db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Model obiektu atramentowego: Windows Forms i COM, a WPF

Istnieją zasadniczo trzy platformy, które obsługują elektroniczne pismo odręczne: platforma formularzy systemu Windows na komputerze typu Tablet, platforma typu Tablet PC COM i [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] platformy.  Formularze systemu Windows i COM udziału platformy podobne modelu obiektu, ale obiekt model [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy różni się znacząco.  W tym temacie omówiono różnice w wysokiego poziomu, dzięki czemu deweloperzy, które działały w jeden obiekt modelu mogą lepiej zrozumieć innych.  
  
## <a name="enabling-ink-in-an-application"></a>Włączanie pismo odręczne w aplikacji  
 Wszystkie trzy platformy są dostarczane obiekty i formantami, które umożliwiają aplikacji na odbieranie danych wejściowych z pióra.  Formularze systemu Windows i platform COM są dostarczane z [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) i [ Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) klasy.  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) i [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) formantów, które można dodać do aplikacji w celu zbierania odręczne.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) i [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) można dołączyć do istniejącego okna Włącz odręczne systemu windows i kontrolki niestandardowe.  
  
 Obejmuje platformy WPF <xref:System.Windows.Controls.InkCanvas> formantu.  Możesz dodać <xref:System.Windows.Controls.InkCanvas> do aplikacji i rozpocząć zbieranie odręczne natychmiast. Z <xref:System.Windows.Controls.InkCanvas>, użytkownik może kopiować, wybierz i zmienianie rozmiaru pisma odręcznego.  Można dodać inne formanty do <xref:System.Windows.Controls.InkCanvas>, a użytkownik może można pisać za pośrednictwem tych kontrolek za.  Włączone odręczne formantu niestandardowego można utworzyć przez dodanie <xref:System.Windows.Controls.InkPresenter> go i pobierania jej punktach pióra.  
  
 W poniższej tabeli wymieniono miejsca dowiedzieć się więcej na temat włączania pismo odręczne w aplikacji:  
  
|W tym celu...|Na platformie WPF...|Na platformach Windows Forms/COM...|  
|-----------------|--------------------------|------------------------------------------|  
|Dodawanie formantu włączone odręczne do aplikacji|Zobacz [wprowadzenie odręczne](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).|Zobacz [oświadczeń automatycznie tworzą próbki](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|Włącz pismo odręczne na kontrolkę niestandardową|Zobacz [tworzenie odręcznego wejściowych kontroli](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).|Zobacz [odręczne próbki Schowka](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff).|  
  
## <a name="ink-data"></a>Odręczne danych  
 Formularze systemu Windows i platform COM [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), i [ Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) każdego Uwidacznianie [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) obiektu. [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) obiekt zawiera dane co najmniej jednej [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) obiekty i udostępnia typowe metody i właściwości do zarządzania i manipulowania tymi pociągnięć.  [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) obiektu zarządza czasem istnienia pociągnięć zawiera; [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) obiektu tworzy i usuwa pociągnięć, które jest właścicielem.  Każdy [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) ma identyfikator, który jest unikatowy w ramach jego elementu nadrzędnego [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) obiektu.  
  
 Na platformie WPF <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> klasy jest właścicielem i zarządza własną okres istnienia. Grupa <xref:System.Windows.Ink.Stroke> obiekty mogą być zebrane w <xref:System.Windows.Ink.StrokeCollection>, który udostępnia metody dla odręczne typowych operacji zarządzania danych takich jak trafień testowania, wymazywanie, przekształcanie i serializacji pismo odręczne. A <xref:System.Windows.Ink.Stroke> mogą należeć do zera, co najmniej jeden <xref:System.Windows.Ink.StrokeCollection> dają obiektów w każdej.  Zamiast [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) obiektu <xref:System.Windows.Controls.InkCanvas> i <xref:System.Windows.Controls.InkPresenter> zawierają <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Para następujące ilustracje porównuje modele obiektów danych odręczne.  Formularze systemu Windows i platform COM [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) obiektu ogranicza okres istnienia [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) obiektów i pakietów pióro należą do poszczególnych pociągnięć.  Co najmniej dwa pociągnięć może odwoływać się takie same [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) obiektów, jak pokazano na poniższej ilustracji.  
  
 ![Diagram odręczne obiektu modelu COM &#47; Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], każdy <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> jest typowe obiektu środowiska wykonawczego języka, który istnieje, tak długo, jak długo element ma odwołanie do niej.  Każdy <xref:System.Windows.Ink.Stroke> odwołania <xref:System.Windows.Input.StylusPointCollection> i <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> obiektu, które są również wspólnych obiektów środowiska uruchomieniowego języka.  
  
 ![Diagram modelu obiektów pisma odręcznego dla WPF. ] (../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 W poniższej tabeli porównano sposobu wykonywania niektórych typowych zadań na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy i formularze systemu Windows i COM platformy.  
  
|Zadanie|Windows Presentation Foundation|Formularze systemu Windows i COM|  
|----------|-------------------------------------|---------------------------|  
|Zapisz odręcznego|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|Odręczne obciążenia|Utwórz <xref:System.Windows.Ink.StrokeCollection> z <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> konstruktora.|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|Testu trafienia|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|Kopiuj pismo odręczne|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|Wklejanie pisma odręcznego|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|Dostęp do właściwości niestandardowe kolekcja strokes|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>(właściwości są przechowywane wewnętrznie i dostępne za pośrednictwem <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, i <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Użyj [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>Udostępnianie odręczne między platformami  
 Mimo że platformy inny obiekt modeli danych odręczne, udostępniania danych między platformy jest bardzo proste. Poniższe przykłady odręczne z aplikacji formularzy systemu Windows i załadować pismo odręczne do aplikacji Windows Presentation Foundation.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Poniższe przykłady odręczne z aplikacji Windows Presentation Foundation i załadować pismo odręczne do aplikacji formularzy systemu Windows.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Zdarzenia z pióra  
 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), i [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) w formularzach systemu Windows i COM platform odbierać zdarzenia podczas użytkownika dane wejściowe pióra danych.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) lub [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) jest dołączona do okna lub formantu i mogą subskrybować zdarzenia wygenerowane przez dane wejściowe typu tablet.  Wątek, w którym występuje te zdarzenia zależy od tego, czy zdarzenia są wywoływane przy użyciu pióra, myszy, lub programowo.  Aby uzyskać więcej informacji na temat wątkowość w odniesieniu do tych zdarzeń, zobacz [Ogólne zagadnienia wątkowość](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) i [wątki na mogą wyzwalać zdarzenia](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).  
  
 Na platformie Windows Presentation Foundation <xref:System.Windows.UIElement> klasa ma zdarzeń przy piórem. Oznacza to, że każdego formantu przedstawia pełny zestaw zdarzeń pióra.  Zdarzenia pióro ma tunelowania propagacji zdarzenia pary i zawsze wykonywane w wątku aplikacji.  Aby uzyskać więcej informacji, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Na poniższym diagramie przedstawiono porównanie modeli obiektów dla klas, które uruchamiają zdarzenia pióra. Model obiektów Windows Presentation Foundation zawiera tylko zdarzenia propagacji, a nie tunelowania odpowiedników zdarzeń.  
  
 ![Diagram z porównaniem zdarzeń w WPF i Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Dane pióra  
 Wszystkie trzy platformy umożliwiają sposoby przechwytywania i manipulowanie danymi wchodzącej z pióra.  Na formularzach systemu Windows i platform COM, jest to osiągane przez utworzenie [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx), związane z nim okna lub formantu i Tworzenie klasy, która implementuje [ Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) lub [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) interfejsu. Niestandardowe wtyczka jest dodawane do kolekcji wtyczki [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx). Aby uzyskać więcej informacji na temat modelu obiektowego, zobacz [Architektura interfejsów API StylusInput](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4).  
  
 Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platformy, <xref:System.Windows.UIElement> klasy udostępnia kolekcję dodatków plug-in, podobne w projekcie ma [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).  Przechwycenia pióra danych, Utwórz klasę, która dziedziczy <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i dodać obiektu do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji <xref:System.Windows.UIElement>. Aby uzyskać więcej informacji na temat interakcji, zobacz [przechwycenia danych wejściowych z pióro](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).  
  
 Na wszystkich platformach puli wątków odbiera dane odręcznego za pomocą pióra zdarzeń i wysyła je do wątku aplikacji.  Aby uzyskać więcej informacji na temat wątków na platformach systemu Windows i modelu COM, zobacz [wątkowość zagadnienia związane z interfejsów API StylusInput](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f).  Aby uzyskać więcej informacji o wątków na prezentacji oprogramowania systemu Windows, temacie [Model wątkowy odręczne](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  
  
 Poniższa ilustracja porównanie modeli obiektów dla klas, które odbierać dane pióra w puli wątków pióra.  
  
 ![Diagram StylusPlugin modelu WPF i Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")
