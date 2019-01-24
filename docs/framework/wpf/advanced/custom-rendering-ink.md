---
title: Niestandardowy atrament renderowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 4aa646ab27044bc26f3787d3edb5f0f15a15bd2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635590"
---
# <a name="custom-rendering-ink"></a>Niestandardowy atrament renderowania
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Właściwości pociągnięcia umożliwia określenie wyglądu pociągnięcia, takie jak rozmiar, kolor i kształt, ale mogą zaistnieć sytuacje, które chcesz dostosować wygląd poza to, co <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Zezwalaj. Można dostosować wygląd pisma odręcznego za renderowaniem w wygląd Aerograf, paint ropa naftowa i innych skutków. Windows Presentation Foundation (WPF) pozwala na niestandardowe renderowanie pisma odręcznego poprzez implementację niestandardową <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i <xref:System.Windows.Ink.Stroke> obiektu.  
  
 Ten temat zawiera następujące podsekcje:  
  
-   [Architektura](#Architecture)  
  
-   [Implementowanie dynamicznych programu renderującego](#ImplementingADynamicRenderer)  
  
-   [Implementowanie niestandardowego pociągnięcia](#ImplementingCustomStrokes)  
  
-   [Implementowanie niestandardowego InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [Podsumowanie](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 Renderowanie pisma odręcznego występuje dwa razy; gdy użytkownik zapisuje pisma odręcznego powierzchnię pisma odręcznego i ponownie po obrysu jest dodawany do powierzchnią. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Renderuje pismo odręczne, gdy użytkownik przesuwa pióra na dyskretyzatorze i <xref:System.Windows.Ink.Stroke> renderowany po dodaniu go do elementu.  
  
 Istnieją trzy klasy do zaimplementowania podczas dynamiczne renderowanie pisma odręcznego.  
  
1.  **DynamicRenderer**: Implementowanie klasy, która pochodzi od klasy <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Ta klasa jest wyspecjalizowanego <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> która renderuje obrysu zgodnie z jej rysowania. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Jest renderowanie w oddzielnym wątku, więc powierzchni pisma odręcznego pojawia się na zbieranie pisma odręcznego, nawet wtedy, gdy wątek interfejsu użytkownika aplikacji jest zablokowany. Aby uzyskać więcej informacji na temat modelu wątkowości, zobacz [Model wątkowości typu atrament](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md). Aby dostosować dynamiczne renderowanie pociągnięcia, należy zastąpić <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metody.  
  
2.  **Pociągnięcia**: Implementowanie klasy, która pochodzi od klasy <xref:System.Windows.Ink.Stroke>. Ta klasa jest odpowiedzialny za statyczne renderowanie <xref:System.Windows.Input.StylusPoint> danych po został przekształcony w <xref:System.Windows.Ink.Stroke> obiektu. Zastąp <xref:System.Windows.Ink.Stroke.DrawCore%2A> metoda zapewnienie tego statyczne renderowania obrysu jest spójna z renderowania dynamicznego.  
  
3.  **Inkcanvas —:** Implementowanie klasy, która pochodzi od klasy <xref:System.Windows.Controls.InkCanvas>. Przypisz dostosowane <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwości. Zastąpienie <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metody i dodać niestandardowe obrysu <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości. Zapewnia to, że wygląd pisma odręcznego są spójne.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Implementowanie dynamicznych programu renderującego  
 Mimo że <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> klasa jest wchodzi w skład [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], wykonywać więcej wyspecjalizowanym renderowania, należy utworzyć dostosowane dynamiczne modułu renderowania, która pochodzi od klasy <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i zastąpić <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metody.  
  
 W poniższym przykładzie pokazano dostosowany <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> który rysuje atrament za pomocą efekt pędzel gradientów liniowych.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Implementowanie niestandardowego pociągnięcia  
 Implementowanie klasy, która pochodzi od klasy <xref:System.Windows.Ink.Stroke>. Ta klasa jest odpowiedzialny za renderowania <xref:System.Windows.Input.StylusPoint> danych po został przekształcony w <xref:System.Windows.Ink.Stroke> obiektu. Zastąp <xref:System.Windows.Ink.Stroke.DrawCore%2A> klasie w celu wykonania rzeczywistego rysowania.  
  
 Klasa obrysu można również przechowywać dane niestandardowe przy użyciu <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> metody. Te dane są przechowywane danymi obrysu utrwalone.  
  
 <xref:System.Windows.Ink.Stroke> Klasy można również wykonać testowanie trafień. Możesz również wdrożyć własne trafień testowania algorytm przez zastąpienie <xref:System.Windows.Ink.Stroke.HitTest%2A> metody w bieżącej klasie.  
  
 Następujące C# kod pokazuje niestandardowy <xref:System.Windows.Ink.Stroke> klasę, która renderuje <xref:System.Windows.Input.StylusPoint> dane jako 3-obrysu.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Implementowanie niestandardowego InkCanvas  
 Najprostszym sposobem użycia dostosowanym <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i obrysu jest implementacja klasy, która pochodzi od klasy <xref:System.Windows.Controls.InkCanvas> i używa tych klas. <xref:System.Windows.Controls.InkCanvas> Ma <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwość, która określa sposób renderowania obrysu po użytkownik jest jego narysowaniu.  
  
 Niestandardowe renderowanie pociągnięć na <xref:System.Windows.Controls.InkCanvas> wykonaj następujące czynności:  
  
-   Utwórz klasę, która pochodzi od klasy <xref:System.Windows.Controls.InkCanvas>.  
  
-   Przypisz dostosowanym <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> właściwości.  
  
-   Zastąp <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metody. W przypadku tej metody należy usunąć oryginalny obrys, który został dodany do przez obiekt InkCanvas. Następnie utwórz obrysu niestandardowego, dodaj ją do <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwość i wywołanie klasy bazowej z nową <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> zawierający niestandardowe obrysu.  
  
 Następujące C# kod pokazuje niestandardowy <xref:System.Windows.Controls.InkCanvas> klasę, która korzysta z niestandardową <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i zbieranie pociągnięć niestandardowych.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> Może mieć więcej niż jeden <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Można dodawać wiele <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obiekty do <xref:System.Windows.Controls.InkCanvas> przez dodanie ich do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Można dostosować wygląd pisma odręcznego wyprowadzanie własne <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, i <xref:System.Windows.Controls.InkCanvas> klasy. Razem te klasy upewnij się, że wygląd obiektu stroke zgodne po użytkownik wprowadzi obrysu i po ich zebraniu.  
  
## <a name="see-also"></a>Zobacz także
- [Zaawansowana obsługa pisma odręcznego](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
