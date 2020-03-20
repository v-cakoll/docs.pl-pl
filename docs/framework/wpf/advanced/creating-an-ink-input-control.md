---
title: Tworzenie formantu danych wejściowych atramentu
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186293"
---
# <a name="creating-an-ink-input-control"></a>Tworzenie formantu danych wejściowych atramentu
Można utworzyć formant niestandardowy, który dynamicznie i statycznie renderuje atrament. Oznacza to, że renderowanie pisma odręcznego jako użytkownik rysuje obrys, co powoduje, że atrament wydaje się "przepływać" z pióra cyfrowego i wyświetlać atrament po dodaniu go do formantu za pomocą pióra cyfrowego, wklejenia ze Schowka lub załadowania z pliku. Aby dynamicznie renderować atrament, formant musi używać pliku <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Aby statycznie renderować atrament, należy zastąpić metody zdarzeń<xref:System.Windows.UIElement.OnStylusDown%2A> <xref:System.Windows.UIElement.OnStylusMove%2A>pisaka <xref:System.Windows.UIElement.OnStylusUp%2A>( <xref:System.Windows.Input.StylusPoint> , , i ), aby <xref:System.Windows.Controls.InkPresenter> zbierać dane, tworzyć obrysy i dodawać je do (który renderuje atrament na formancie).  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Jak: Zbieranie danych punktu rysika i tworzenie pociągnięć odręcznych](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Jak: Włącz formant, aby zaakceptować dane wejściowe z myszy](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Połączenie go](#PuttingItTogether)  
  
- [Korzystanie z dodatkowych wtyczek i dynamicznych głośników](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Podsumowanie](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Jak: Zbieranie danych punktu rysika i tworzenie pociągnięć odręcznych  
 Aby utworzyć formant, który zbiera i zarządza pociągnięć odręcznych, wykonaj następujące czynności:  
  
1. Wyprowadzić klasę <xref:System.Windows.Controls.Control> z lub jedną z <xref:System.Windows.Controls.Control>klas pochodnych , takich jak <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Dodaj <xref:System.Windows.Controls.InkPresenter> do klasy i <xref:System.Windows.Controls.ContentControl.Content%2A> ustaw właściwość <xref:System.Windows.Controls.InkPresenter>na nowy .  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Dołącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do, <xref:System.Windows.Controls.InkPresenter> wywołując <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> metodę i dodaj <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do kolekcji. <xref:System.Windows.UIElement.StylusPlugIns%2A> Dzięki temu <xref:System.Windows.Controls.InkPresenter> można wyświetlić atrament jako dane punktu pisaka są zbierane przez formant.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Zastąd <xref:System.Windows.UIElement.OnStylusDown%2A> w tej metodzie.  W tej metodzie przechwyć <xref:System.Windows.Input.Stylus.Capture%2A>rysik za pomocą wywołania . Przechwytując rysik, formant będzie nadal <xref:System.Windows.UIElement.StylusMove> odbierać i <xref:System.Windows.UIElement.StylusUp> zdarzenia, nawet jeśli pisak opuszcza granice formantu. Nie jest to ściśle obowiązkowe, ale prawie zawsze pożądane dla dobrego doświadczenia użytkownika. Utwórz <xref:System.Windows.Input.StylusPointCollection> nowy, <xref:System.Windows.Input.StylusPoint> aby zebrać dane. Na koniec dodaj początkowy <xref:System.Windows.Input.StylusPoint> zestaw danych <xref:System.Windows.Input.StylusPointCollection>do pliku .  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Zastąd <xref:System.Windows.UIElement.OnStylusMove%2A> w tej <xref:System.Windows.Input.StylusPoint> metodzie <xref:System.Windows.Input.StylusPointCollection> i dodaj dane do obiektu utworzonego wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Zastąd <xref:System.Windows.UIElement.OnStylusUp%2A> w tej <xref:System.Windows.Ink.Stroke> metodzie <xref:System.Windows.Input.StylusPointCollection> i utwórz nową z danymi. Dodaj nowy <xref:System.Windows.Ink.Stroke> utworzony do <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekcji <xref:System.Windows.Controls.InkPresenter> i wydania przechwytywania rysika.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Jak: Włącz formant, aby zaakceptować dane wejściowe z myszy  
 Jeśli dodasz poprzedni formant do aplikacji, uruchom go i użyj myszki jako urządzenia wejściowego, można zauważyć, że obrysy nie są utrwalone. Aby utrwalić pociągnięcia, gdy mysz jest używana jako urządzenie wejściowe, wykonaj następujące czynności:  
  
1. Zastądnie <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> i <xref:System.Windows.Input.StylusPointCollection> utwórz nowe Pobierz położenie myszy, gdy <xref:System.Windows.Input.StylusPoint> wystąpiło zdarzenie i <xref:System.Windows.Input.StylusPoint> utwórz przy użyciu danych punktowych i dodaj je do <xref:System.Windows.Input.StylusPointCollection>pliku .  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Zastąd <xref:System.Windows.UIElement.OnMouseMove%2A> w tej metodzie. Pobierz położenie myszy, gdy wystąpiło zdarzenie <xref:System.Windows.Input.StylusPoint> i utwórz przy użyciu danych punktowych.  Dodaj <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection> obiektu, który został utworzony wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Zastąd <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> w tej metodzie.  Utwórz <xref:System.Windows.Ink.Stroke> nowy <xref:System.Windows.Input.StylusPointCollection> z danymi i <xref:System.Windows.Ink.Stroke> dodaj nowy <xref:System.Windows.Controls.InkPresenter.Strokes%2A> utworzony do <xref:System.Windows.Controls.InkPresenter>kolekcji .  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>Połączenie go  
 Poniższy przykład jest formantem niestandardowym, który zbiera atrament, gdy użytkownik używa myszy lub pióra.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Korzystanie z dodatkowych wtyczek i dynamicznych głośników  
 Podobnie jak InkCanvas, formant <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> niestandardowy <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> może mieć niestandardowe i dodatkowe obiekty. Dodaj je <xref:System.Windows.UIElement.StylusPlugIns%2A> do kolekcji. Kolejność <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> obiektów w pliku <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> wpływa na wygląd pisma odmłkowego podczas renderowania. Załóżmy, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> `dynamicRenderer` że masz <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> `translatePlugin` wywołane i niestandardowe wywołane, które odsuwa atrament od pióra cyfrowego. Jeśli `translatePlugin` jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> pierwszy <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>w `dynamicRenderer` , i jest drugim, atrament, który "przepływa" zostanie przesunięty, jak użytkownik przesuwa pióro. Jeśli `dynamicRenderer` jest pierwszy, a `translatePlugin` jest drugi, atrament nie zostanie odsunięty, dopóki użytkownik nie podniesie pióra.  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>Podsumowanie  
 Formant, który zbiera i renderuje atrament, zastępując metody zdarzenia pisaka. Tworząc własną kontrolę, wyprowadzając własne <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> klasy i wstawiając je do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, można zaimplementować praktycznie każde zachowanie, jakie można sobie wyobrazić za pomocą atramentu cyfrowego. Masz dostęp do <xref:System.Windows.Input.StylusPoint> danych, jak jest generowany, co <xref:System.Windows.Input.Stylus> daje możliwość dostosowania danych wejściowych i renderowania go na ekranie, zgodnie z odpowiednimi dla aplikacji. Ponieważ masz taki niski poziom <xref:System.Windows.Input.StylusPoint> dostępu do danych, można zaimplementować zbieranie pisma odmłkowego i renderowania go z optymalną wydajnością dla aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowana obsługa atramentu](advanced-ink-handling.md)
- [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
