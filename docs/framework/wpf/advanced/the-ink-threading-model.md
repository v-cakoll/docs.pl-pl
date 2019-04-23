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
ms.openlocfilehash: 80e7ef202c46a23069766512cf4e67bb21a49564
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335325"
---
# <a name="the-ink-threading-model"></a>Model wątkowości typu atrament
Jest jedną z zalet pisma odręcznego na komputerze typu Tablet, może się wydawać, bardzo podobnie jak za pomocą regularnego pióra i dokument.  Aby to osiągnąć, Pióro zbiera dane wejściowe stawki znacznie wyższa niż myszy i renderuje pismo odręczne jako zapisy użytkownika.  Wątek interfejsu użytkownika aplikacji nie wystarcza do zbierania danych pióra i renderowanie pisma odręcznego, ponieważ może zostać zablokowany.  Aby rozwiązać tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja używa dwa dodatkowe wątki, gdy użytkownik zapisze pisma odręcznego.  
  
 Na poniższej liście opisano wątków, które wzięcia udziału w zbieraniu i cyfrowy atrament renderowania:  
  
-   Wątek pióra - wątku, który akceptuje dane wejściowe z pisaka  (W rzeczywistości jest to z puli wątków, ale w tym temacie odnosi się do niego jako wątek pióra).  
  
-   Wątek interfejsu użytkownika aplikacji — wątku, który określa interfejs użytkownika aplikacji.  
  
-   Wątek renderowania dynamicznego - wątku, który renderuje pismo odręczne, gdy użytkownik rysuje obrysu. Wątek renderowania dynamicznego różni się od wątku, który renderuje inne elementy interfejsu użytkownika dla aplikacji, jak wspomniano w programie Windows Presentation Foundation [Model wątkowy](threading-model.md).  
  
 Model pisma odręcznego jest taki sam, czy aplikacja używa <xref:System.Windows.Controls.InkCanvas> lub formant niestandardowy, podobne do pokazanego na [tworzenie kontrolki danych wejściowych pisma odręcznego](creating-an-ink-input-control.md).  Mimo że w tym temacie omówiono wielowątkowości w <xref:System.Windows.Controls.InkCanvas>, Zastosuj te same pojęcia, podczas tworzenia niestandardowego formantu.  
  
## <a name="threading-overview"></a>Wątkowość — omówienie  
 Na poniższym diagramie przedstawiono model wątkowości, gdy użytkownik rysuje pociągnięcia:  
  
 ![Model wątkowości podczas rysowania pociągnięcia. ](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1. Akcjami występującymi podczas, gdy użytkownik wprowadzi pociągnięcia  
  
    1.  Gdy użytkownik wprowadzi pociągnięcia, punkty pióra mają na wątek pióra.  Pióro dodatków plug-in, w tym <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>Zaakceptuj punktów pióra na wątek pióra i szansę zmodyfikuj je przed <xref:System.Windows.Controls.InkCanvas> otrzymuje je.  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Renderuje punktów pióra na wątek renderowania dynamicznego. Dzieje się w tym samym czasie co w poprzednim kroku.  
  
    3.  <xref:System.Windows.Controls.InkCanvas> Otrzymuje punkty pióra przez wątek interfejsu użytkownika.  
  
2. Akcje, które pojawiają się po użytkownik kończy pociągnięcia  
  
    1.  Gdy użytkownik zakończy rysowania pociągnięcia <xref:System.Windows.Controls.InkCanvas> tworzy <xref:System.Windows.Ink.Stroke> obiektu i dodaje go do <xref:System.Windows.Controls.InkPresenter>, która statycznie renderuje.  
  
    2.  Alerty wątku interfejsu użytkownika <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderowany obrysu statycznie, więc <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> usuwa jego wizualnej reprezentacji obiektu stroke.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Zbieranie pisma odręcznego i dodatki plug-in pióra  
 Każdy <xref:System.Windows.UIElement> ma <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Obiekty w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> odbierania i może być modyfikowana pióro punktów danych na wątek pióra. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Obiekty otrzymują punktów pióra, zgodnie z ich kolejność w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 Na poniższym diagramie przedstawiono hipotetyczny problem gdzie <xref:System.Windows.UIElement.StylusPlugIns%2A> zbiór <xref:System.Windows.UIElement> zawiera `stylusPlugin1`, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, i `stylusPlugin2`, w tej kolejności.  
  
 ![Kolejność pióro wtyczki wpływają na dane wyjściowe. ](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 Na poprzednim rysunku następujące zachowanie ma miejsce:  
  
1. `StylusPlugin1` Modyfikuje wartości x i y.  
  
2. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odbiera punktów zmodyfikowane pióra i renderuje je na wątek renderowania dynamicznego.  
  
3. `StylusPlugin2` odbiera punktów zmodyfikowane pióra i dalsze Modyfikuje wartości x i y.  
  
4. Aplikacji umożliwia zbieranie informacji o punktach pióra i, gdy użytkownik zakończy obrysu statycznie renderuje obrysu.  
  
 Załóżmy, że `stylusPlugin1` ogranicza punktów pióro prostokąt i `stylusPlugin2` tłumaczy punktów pióro po prawej stronie.  W poprzednim scenariuszu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> otrzymuje punkty pióro ograniczony, ale nie wskazuje przetłumaczone pióra.  Gdy użytkownik wprowadzi obrysu, obrysu jest renderowany w granicach prostokąt, ale obrysu nie pojawia się do tłumaczenia użytkownika podnosi pióra.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Wykonywanie operacji za pomocą pióra wtyczkę w wątku interfejsu użytkownika  
 Ponieważ nie można wykonać dokładne testowania trafień na wątek pióra, niektóre elementy od czasu do czasu może pojawić się wejście pióra przeznaczonych do innych elementów. Jeśli musisz upewnić się, czy dane wejściowe został rozesłany prawidłowo, przed wykonaniem operacji subskrybować i wykonaj operację w <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, lub <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> metody. Te metody są wywoływane przez wątek aplikacji po dokładne testowania trafień została wykonana. Aby subskrybować tych metod, należy wywołać <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> metody w metodzie, która występuje na wątek pióra.  
  
 Na poniższym diagramie przedstawiono relację między wątek pióra i wątku interfejsu użytkownika w odniesieniu do zdarzeń pióra <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![Modele wątkowości pisma odręcznego &#40;interfejsu użytkownika i pióra&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Renderowanie pisma odręcznego  
 Jako użytkownik wprowadzi obrysu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderuje pismo odręczne w oddzielnym wątku, więc pisma odręcznego pojawia się na "flow" z pióra nawet wtedy, gdy wątek interfejsu użytkownika jest zajęty.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Oparta na wątek renderowania dynamicznego drzewa wizualnego, zbiera dane punktów pióra.  Gdy użytkownik zakończy obrysu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> pyta otrzymywać powiadomienia, gdy aplikacja wykonuje następny przebieg renderowania.  Po jej zakończeniu przebiegu renderowania następnej <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> czyści jego drzewa wizualnego.  Na poniższym diagramie przedstawiono ten proces.  
  
 ![Diagram wątkowości pisma odręcznego](./media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1. Użytkownik rozpoczyna stroke.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Tworzy drzewo wizualne.  
  
2. Użytkownik jest rysowanie stroke.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Tworzy drzewo wizualne.  
  
3. Użytkownik kończy się stroke.  
  
    1.  <xref:System.Windows.Controls.InkPresenter> Dodaje skok do jego drzewa wizualnego.  
  
    2.  Warstwa integracji nośnika (MIL) renderuje statycznie pociągnięć.  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Czyści elementy wizualne.
