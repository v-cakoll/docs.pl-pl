---
title: Model wątkowości typu atrament
ms.date: 03/30/2017
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
ms.openlocfilehash: cc0ff8a2345bd945dd2fffdfda80f00e1ab99c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547882"
---
# <a name="the-ink-threading-model"></a>Model wątkowości typu atrament
Jedną z zalet pismo odręczne na komputerze typu Tablet jest, że go wydaje się znacznie zapisu przy użyciu pióra regularnych i papieru.  W tym celu pióra zbiera dane wejściowe szybkością znacznie wyższa niż myszy i renderuje pismo odręczne jako zapisy użytkownika.  Wątek interfejsu użytkownika aplikacji nie jest wystarczające do zbierania danych pióra i odręcznego renderowania, ponieważ mogą zostać zablokowane.  Aby rozwiązać, to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja używa dwóch dodatkowych wątków, gdy użytkownik zapisuje odręczne.  
  
 Poniższa lista zawiera opis wątków, które uczestniczą w zbierania i renderowania elektroniczne pismo odręczne:  
  
-   Wątek pióra - wątku, który pobiera pióra.  (W rzeczywistości jest to puli wątków, ale w tym temacie odnosi się do niego jako wątku pióra).  
  
-   Wątek interfejsu użytkownika aplikacji - wątku, który określa interfejs użytkownika aplikacji.  
  
-   Dynamiczne renderowanie wątku - wątku, który renderuje pismo odręczne, gdy użytkownik rysuje pociągnięcia. Wątek dynamicznego renderowania różni się od wątku, który renderuje inne elementy interfejsu użytkownika dla aplikacji, jak wspomniano w Windows Presentation Foundation [Model wątkowy](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
 Model pisma odręcznego jest taki sam, czy aplikacja używa <xref:System.Windows.Controls.InkCanvas> lub kontrolkę niestandardową, podobnie jak w [Tworzenie formantu danych wejściowych odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  Mimo że w tym temacie omówiono wątkowość w postaci liczby <xref:System.Windows.Controls.InkCanvas>, te same pojęcia zastosować podczas tworzenia niestandardowego formantu.  
  
## <a name="threading-overview"></a>Wątkowość — omówienie  
 Na poniższym diagramie przedstawiono model wątkowości, gdy użytkownik rysuje pociągnięcia:  
  
 ![Model wątkowości podczas rysowania pociągnięcia. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1.  Występuje, gdy użytkownik wprowadzi obrysu akcje  
  
    1.  Gdy użytkownik wprowadzi pociągnięcia, punkty pióro mają w wątku pióra.  Pióro dodatków plug-in, łącznie z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, Zaakceptuj punktów Pióro w wątku pióra i w sposób, aby zmodyfikować je przed <xref:System.Windows.Controls.InkCanvas> odbiera je.  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Renderuje punktów Pióro w wątku renderowania dynamicznych. Dzieje się w tym samym czasie, co w poprzednim kroku.  
  
    3.  <xref:System.Windows.Controls.InkCanvas> Odbiera punktów Pióro w wątku interfejsu użytkownika.  
  
2.  Akcje występujące po zakończeniu obrysu użytkownika  
  
    1.  Gdy użytkownik zakończy rysowania obrysu, <xref:System.Windows.Controls.InkCanvas> tworzy <xref:System.Windows.Ink.Stroke> obiektu i dodaje go do <xref:System.Windows.Controls.InkPresenter>, które statycznie renderuje.  
  
    2.  Alerty wątku interfejsu użytkownika <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obrysu statycznie renderowany, więc <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> spowoduje usunięcie jej wizualną reprezentację pociągnięć.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Zbieranie pisma odręcznego i wtyczek pióra  
 Każdy <xref:System.Windows.UIElement> ma <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Obiekty w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> odbierania i może być modyfikowana punktów Pióro w wątku pióra. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Obiektów uzyskuje punkty pióro zgodnie z ich kolejność, w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 Na poniższym diagramie przedstawiono hipotetyczny sytuacji gdy <xref:System.Windows.UIElement.StylusPlugIns%2A> Kolekcja <xref:System.Windows.UIElement> zawiera `stylusPlugin1`, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, i `stylusPlugin2`, w tym kolejność.  
  
 ![Kolejność wtyczek pióro wpływ na wyniki. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 Na poprzedni diagram następujące zachowanie odbywa się:  
  
1.  `StylusPlugin1` Modyfikuje wartości x i y.  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odbiera punktów pióro zmodyfikowane i renderuje je w wątku renderowania dynamicznych.  
  
3.  `StylusPlugin2` odbiera punktów pióro zmodyfikowane i więcej Modyfikuje wartości x i y.  
  
4.  Aplikacja zbiera punktów Pióro i, gdy użytkownik zakończy obrysu, statycznie renderuje pociągnięć.  
  
 Załóżmy, że `stylusPlugin1` ogranicza pióro punktów prostokąta i `stylusPlugin2` tłumaczy punktów pióro z prawej strony.  W poprzednim scenariuszu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odbiera punkty pióro ograniczone, ale nie punkty przetłumaczonego pióra.  Gdy użytkownik wprowadzi obrysu, obrysu jest renderowany w granicach prostokąta, ale pociągnięcie nie pojawia się do tłumaczenia użytkownika wind pióra.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Wykonywanie operacji z pióra wtyczki w wątku interfejsu użytkownika  
 Ponieważ nie można wykonać dokładne testowanie trafień w wątku pióra, niektóre elementy czasami może pojawić się wprowadzania danych piórem przeznaczonych do innych elementów. Aby się upewnić, że dane wejściowe został poprawnie skierowany przed wykonaniem operacji należy subskrybować i wykonaj operację w <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, lub <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> metody. Te metody są wywoływane przez wątek aplikacji po dokładne testowanie trafień została wykonana. Aby subskrybować tych metod, należy wywołać <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> metody w metodzie, który występuje w wątku pióra.  
  
 Na poniższym diagramie przedstawiono związek między pióra wątku i wątku interfejsu użytkownika w odniesieniu do zdarzeń pióra <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![Modele wątkowości odręczne &#40;interfejsu użytkownika i pióra&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Renderowanie odręcznego  
 Jako użytkownik wprowadzi obrysu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderuje pismo odręczne na oddzielnym wątku, więc odręcznego "przepływ" z pióra nawet wtedy, gdy wątek interfejsu użytkownika jest zajęty.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Utworzy w wątku renderowania dynamicznego drzewa wizualnego zbiera pióro punktów.  Gdy użytkownik zakończy obrysu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> zapyta otrzymywać powiadomienia, gdy aplikacja nie przebiegu renderowania dalej.  Zakończone przebiegu renderowania następnej aplikacji <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> czyści jego drzewie wizualnym.  Na poniższym diagramie przedstawiono ten proces.  
  
 ![Wątkowość diagram odręczne](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1.  Użytkownik rozpoczyna pociągnięć.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Tworzy drzewa wizualnego.  
  
2.  Użytkownik jest rysowania pociągnięć.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Kompilacje drzewa wizualnego.  
  
3.  Użytkownik kończy pociągnięć.  
  
    1.  <xref:System.Windows.Controls.InkPresenter> Dodaje skok do jego drzewie wizualnym.  
  
    2.  Warstwa integracji nośnika (MIL) renderuje statycznie pociągnięć.  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Czyści wizualnych.
