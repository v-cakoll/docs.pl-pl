---
title: Niestandardowy atrament renderowania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8f7288d9d3b729ab9c38bc6b2afd603b4d6d1aa
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="custom-rendering-ink"></a>Niestandardowy atrament renderowania
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Właściwości pociągnięcia umożliwia określenie wyglądu pociągnięcia, takie jak jego rozmiar, kolor i kształt, ale czasami, które chcesz dostosować wygląd poza co <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Zezwalaj. Można dostosować wygląd odręczne przez renderowanie wygląd pędzla lotniczego, paint wydobycie ropy naftowej i innych skutków. Windows Presentation Foundation (WPF) umożliwia niestandardowy renderowania odręczne dzięki implementacji niestandardowego <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i <xref:System.Windows.Ink.Stroke> obiektu.  
  
 Ten temat zawiera następujące podsekcje:  
  
-   [Architektura](#Architecture)  
  
-   [Implementowanie dynamiczne renderowanie](#ImplementingADynamicRenderer)  
  
-   [Implementowanie niestandardowych pociągnięć](#ImplementingCustomStrokes)  
  
-   [Implementowanie niestandardowego InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [Zawierania](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 Renderowanie odręczne występuje dwa razy; gdy użytkownik zapisuje odręczne pisma odręcznego powierzchnię i ponownie po obrysu jest dodawany do powierzchnią. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Renderuje pismo odręczne, gdy użytkownik przesuwa pióra powierzchni dyskretyzatora i <xref:System.Windows.Ink.Stroke> renderowany po dodaniu do elementu.  
  
 Istnieją trzy klasy do zaimplementowania podczas renderowania dynamicznie odręczne.  
  
1.  **DynamicRenderer**: Implementowanie klasy, która pochodzi z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Ta klasa jest specjalistycznej <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> która renderuje pociągnięć podczas wprowadzania. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Jest renderowanie w oddzielnym wątku tak pisma odręcznego powierzchni wydaje się zbieranie odręczne, nawet wtedy, gdy wątek interfejsu użytkownika aplikacji jest zablokowany. Aby uzyskać więcej informacji na temat modelu wątkowości zobacz [Model wątkowy odręczne](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md). Aby dostosować dynamiczne renderowanie pociągnięcia, Zastąp <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metody.  
  
2.  **Obrysu**: Implementowanie klasy, która pochodzi z <xref:System.Windows.Ink.Stroke>. Ta klasa jest odpowiedzialny za statyczne renderowanie <xref:System.Windows.Input.StylusPoint> danych po przekonwertowaniu do <xref:System.Windows.Ink.Stroke> obiektu. Zastąpienie <xref:System.Windows.Ink.Stroke.DrawCore%2A> metodę, aby zapewnić tym statycznych renderowania obrysu jest zgodna z dynamicznego renderowania.  
  
3.  **InkCanvas:** zaimplementować klasę pochodzącą z <xref:System.Windows.Controls.InkCanvas>. Przypisz dostosowywane <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwości. Zastąpienie <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> — metoda i dodać niestandardowe obrysu <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości. Dzięki temu, że wygląd pisma odręcznego są spójne.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Implementowanie dynamiczne renderowanie  
 Mimo że <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> klasy jest częścią standardowej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], przeprowadzać więcej specjalizowany renderowania, należy utworzyć dostosowane dynamiczny moduł renderowania, pochodzącą z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i zastąpić <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> — metoda.  
  
 W poniższym przykładzie pokazano dostosowany <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> który rysuje odręczne z efektem pędzla gradientu liniowego.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Implementowanie niestandardowych pociągnięć  
 Implementuje klasę, która jest pochodną <xref:System.Windows.Ink.Stroke>. Ta klasa jest odpowiedzialny za renderowania <xref:System.Windows.Input.StylusPoint> danych po przekonwertowaniu do <xref:System.Windows.Ink.Stroke> obiektu. Zastąpienie <xref:System.Windows.Ink.Stroke.DrawCore%2A> klasy do rzeczywistego rysunku.  
  
 Klasa obrysu można przechowywać danych niestandardowych za pomocą <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> metody. Dane te są przechowywane danymi obrysu utrwalone.  
  
 <xref:System.Windows.Ink.Stroke> Klasy można także przeprowadzić testowanie trafień. Można też wdrożyć własne trafień testowania algorytm przez zastąpienie <xref:System.Windows.Ink.Stroke.HitTest%2A> metody w bieżącej klasie.  
  
 Poniższy kod C# przedstawia niestandardowego <xref:System.Windows.Ink.Stroke> klasy, który renderuje <xref:System.Windows.Input.StylusPoint> dane jako 3-stroke.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Implementowanie niestandardowego InkCanvas  
 Najprostszym sposobem, aby korzystać z dostosowanego <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i obrysu jest implementacja klasy, która jest pochodną <xref:System.Windows.Controls.InkCanvas> i używa tych klas. <xref:System.Windows.Controls.InkCanvas> Ma <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwość, która określa, jak jest renderowany obrysu, gdy użytkownik jest rysowania.  
  
 Niestandardowy renderowania pociągnięć <xref:System.Windows.Controls.InkCanvas> wykonaj następujące czynności:  
  
-   Utwórz klasę pochodną <xref:System.Windows.Controls.InkCanvas>.  
  
-   Przypisz z dostosowanych <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> właściwości.  
  
-   Zastąpienie <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metody. W przypadku tej metody należy usunąć obrysu oryginalnej, która została dodana do przez obiekt InkCanvas. Następnie utwórz niestandardowe pociągnięcia, dodaj go do <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości i wywołanie klasy podstawowej o nowe <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> zawierający obrysu niestandardowego.  
  
 Poniższy kod C# przedstawia niestandardowego <xref:System.Windows.Controls.InkCanvas> klasy, która używa dostosowany <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i zbiera pociągnięć niestandardowych.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> Może mieć więcej niż jeden <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Można dodawać wiele <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obiekty do <xref:System.Windows.Controls.InkCanvas> przez dodanie ich do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Można dostosować wygląd odręczne wyprowadzanie własne <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, i <xref:System.Windows.Controls.InkCanvas> klasy. Razem te klasy upewnij się, czy wygląd obiektu stroke jest spójne, gdy użytkownik wprowadzi obrysu i po ich zebraniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowana obsługa pisma odręcznego](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
