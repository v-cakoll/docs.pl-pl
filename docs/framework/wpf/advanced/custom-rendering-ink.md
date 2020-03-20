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
ms.openlocfilehash: 3cf0d98c40e71a380b218c76d6e52d00cdd05342
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186349"
---
# <a name="custom-rendering-ink"></a>Niestandardowy atrament renderowania
Właściwość <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> obrysu umożliwia określenie wyglądu obrysu, takiego jak jego rozmiar, kolor i kształt, ale mogą <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> wystąpić czasy, w których chcesz dostosować wygląd poza to, co pozwala. Można dostosować wygląd pisma odcowego, renderując wygląd pędzla powietrznego, farby olejnej i wielu innych efektów. Windows Presentation Foundation (WPF) umożliwia niestandardowe renderowania pisma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Ink.Stroke> od ink przez implementowanie niestandardowe i obiektu.  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Architektura](#Architecture)  
  
- [Implementowanie dynamicznego modułu renderowania](#ImplementingADynamicRenderer)  
  
- [Implementowanie niestandardowych pociągnięć](#ImplementingCustomStrokes)  
  
- [Implementowanie niestandardowego urządzenia InkCanvas](#ImplementingACustomInkCanvas)  
  
- [Podsumowanie](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architektura  
 Renderowanie pisma odurzającego odbywa się dwa razy; gdy użytkownik zapisuje atrament na powierzchni odręcznej i ponownie po dodaniu obrysu do powierzchni z włączoną funkcją pisma odręcznego. Renderuje <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> atrament, gdy użytkownik przesuwa pióro na digitalizatorze, a <xref:System.Windows.Ink.Stroke> renderuje się po dodaniu go do elementu.  
  
 Istnieją trzy klasy do zaimplementowania podczas dynamicznego renderowania pisma odurzającego.  
  
1. **DynamicRenderer**: Implementowanie klasy, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>która wywodzi się z . Ta klasa jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> wyspecjalizowana, która renderuje obrys podczas rysowania. Nie <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderowania na oddzielny wątek, więc powierzchnia pisma od pisma od pisma wydaje się zbierać atramentu, nawet wtedy, gdy interfejs użytkownika aplikacji (UI) wątek jest zablokowany. Aby uzyskać więcej informacji na temat modelu wątkowości, zobacz [Model wątkowości odulcowej](the-ink-threading-model.md). Aby dostosować dynamiczne renderowanie obrysu, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> należy zastąpić metodę.  
  
2. **Stroke**: Zaimplementuj klasę, która wywodzi się z <xref:System.Windows.Ink.Stroke>. Ta klasa jest odpowiedzialna za statyczne renderowanie <xref:System.Windows.Input.StylusPoint> danych po <xref:System.Windows.Ink.Stroke> przekonwertowaniu na obiekt. Zastąpili metodę, <xref:System.Windows.Ink.Stroke.DrawCore%2A> aby upewnić się, że statyczne renderowanie obrysu jest zgodne z renderowaniem dynamicznym.  
  
3. **InkCanvas:** Zaimplementuj <xref:System.Windows.Controls.InkCanvas>klasę, która wywodzi się z . Przypisz dostosowane <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwości. Zastądeń <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metodę i dodaj <xref:System.Windows.Controls.InkCanvas.Strokes%2A> niestandardowy obrys do właściwości. Dzięki temu wygląd atramentu jest spójny.  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>Implementowanie dynamicznego modułu renderowania  
 Chociaż <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> klasa jest standardową [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]częścią , aby wykonać bardziej wyspecjalizowane renderowanie, należy utworzyć <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> niestandardowy moduł <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> renderowania dynamicznego, który wywodzi się z metody i ją zastąpić.  
  
 W poniższym przykładzie <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> pokazano dostosowane, który rysuje pisma odmłkowego z liniowym efektem pędzla gradientu.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>Implementowanie niestandardowych pociągnięć  
 Zaimplementuj <xref:System.Windows.Ink.Stroke>klasę, która wywodzi się z . Ta klasa jest odpowiedzialna <xref:System.Windows.Input.StylusPoint> za renderowanie danych po <xref:System.Windows.Ink.Stroke> przekonwertowaniu na obiekt. Zastądnie klasy, <xref:System.Windows.Ink.Stroke.DrawCore%2A> aby wykonać rzeczywisty rysunek.  
  
 Klasa Stroke może również przechowywać <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> dane niestandardowe przy użyciu metody. Te dane są przechowywane z danymi obrysu po utrwaleniu.  
  
 Klasa <xref:System.Windows.Ink.Stroke> może również wykonać testy trafień. Można również zaimplementować własny algorytm <xref:System.Windows.Ink.Stroke.HitTest%2A> testowania trafień, zastępując metodę w bieżącej klasie.  
  
 Poniższy kod Języka C# <xref:System.Windows.Ink.Stroke> demonstruje <xref:System.Windows.Input.StylusPoint> klasę niestandardową, która renderuje dane jako obrys 3-W.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>Implementowanie niestandardowego urządzenia InkCanvas  
 Najprostszym sposobem użycia dostosowane <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> i stroke jest zaimplementowanie <xref:System.Windows.Controls.InkCanvas> klasy, która pochodzi z i używa tych klas. Ma <xref:System.Windows.Controls.InkCanvas> <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwość, która określa sposób renderowania obrysu podczas rysowania przez użytkownika.  
  
 Aby wykonać niestandardowe <xref:System.Windows.Controls.InkCanvas> pociągnięcia renderowania na wykonaj następujące czynności:  
  
- Utwórz klasę, która <xref:System.Windows.Controls.InkCanvas>wywodzi się z pliku .  
  
- Przypisz dostosowanego <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> do właściwości.  
  
- Zastąd <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> w tej metodzie. W tej metodzie usuń oryginalny obrys, który został dodany do InkCanvas. Następnie utwórz niestandardowy obrys, dodaj go do <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> i wywołaj klasę podstawową z nowym, który zawiera niestandardowy obrys.  
  
 Poniższy kod Języka C# <xref:System.Windows.Controls.InkCanvas> demonstruje klasę <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> niestandardową, która używa dostosowanych i zbiera niestandardowe obrysy.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Może <xref:System.Windows.Controls.InkCanvas> mieć więcej <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>niż jeden . Można dodać <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> wiele obiektów <xref:System.Windows.Controls.InkCanvas> do, dodając <xref:System.Windows.UIElement.StylusPlugIns%2A> je do właściwości.  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Podsumowanie  
 Wygląd pisma oduwu można dostosować, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>wyprowadzając własne , <xref:System.Windows.Ink.Stroke>i <xref:System.Windows.Controls.InkCanvas> klasy. Razem te klasy zapewniają, że wygląd obrysu jest spójny, gdy użytkownik rysuje obrys i po jego zebraniu.  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowana obsługa atramentu](advanced-ink-handling.md)
