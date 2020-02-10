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
ms.openlocfilehash: 98b2abf813a232e36b80683254174b12b97659bb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095219"
---
# <a name="creating-an-ink-input-control"></a>Tworzenie formantu danych wejściowych atramentu
Można utworzyć kontrolkę niestandardową, która dynamicznie i statycznie renderuje pismo odręczne. Oznacza to, że renderowanie pisma odręcznego jako użytkownik rysuje pociągnięcie, powodując, że atrament pojawia się jako "Flow" z pióra tabletu i wyświetli atrament po dodaniu go do kontrolki, za pomocą pióra, wklejonego ze schowka lub załadowanego z pliku. Aby dynamicznie renderować atrament, formant musi używać <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Aby można było statycznie renderować atrament, należy zastępować metody zdarzeń pióra (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>i <xref:System.Windows.UIElement.OnStylusUp%2A>) do zbierania danych <xref:System.Windows.Input.StylusPoint>, tworzenia pociągnięć i dodawania ich do <xref:System.Windows.Controls.InkPresenter> (które renderuje atrament na kontrolce).  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Instrukcje: zbieranie danych z punktów pióra i tworzenie pociągnięć odręcznych](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Instrukcje: Włączanie wprowadzania danych przez formant przy użyciu myszy](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Umieszczanie ich razem](#PuttingItTogether)  
  
- [Korzystanie z dodatkowych wtyczek i DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Podsumowanie](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Instrukcje: zbieranie danych z punktów pióra i tworzenie pociągnięć odręcznych  
 Aby utworzyć formant, który zbiera i zarządza pociągnięciami odręcznymi, wykonaj następujące czynności:  
  
1. Utwórz klasę z <xref:System.Windows.Controls.Control> lub jednej z klas pochodzących od <xref:System.Windows.Controls.Control>, takich jak <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Dodaj <xref:System.Windows.Controls.InkPresenter> do klasy i ustaw właściwość <xref:System.Windows.Controls.ContentControl.Content%2A> na nową <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Dołącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkPresenter> przez wywołanie metody <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> i dodanie <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do kolekcji <xref:System.Windows.UIElement.StylusPlugIns%2A>. Pozwala to <xref:System.Windows.Controls.InkPresenter> na wyświetlanie atramentu jako danych z punktu widzenia przez formant.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Zastąp metodę <xref:System.Windows.UIElement.OnStylusDown%2A>.  W tej metodzie należy przechwycić pióro wywołaniem <xref:System.Windows.Input.Stylus.Capture%2A>. Przechwytując pióro, formant będzie kontynuował odbieranie <xref:System.Windows.UIElement.StylusMove> i zdarzeń <xref:System.Windows.UIElement.StylusUp>, nawet jeśli pióro opuści granice formantu. Nie jest to absolutnie obowiązkowe, ale prawie zawsze jest to konieczne dla dobrego środowiska użytkownika. Utwórz nowy <xref:System.Windows.Input.StylusPointCollection>, aby zebrać dane <xref:System.Windows.Input.StylusPoint>. Na koniec dodaj początkowy zestaw danych <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Zastąp metodę <xref:System.Windows.UIElement.OnStylusMove%2A> i Dodaj dane <xref:System.Windows.Input.StylusPoint> do obiektu <xref:System.Windows.Input.StylusPointCollection> utworzonego wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Zastąp metodę <xref:System.Windows.UIElement.OnStylusUp%2A> i Utwórz nowy <xref:System.Windows.Ink.Stroke> z danymi <xref:System.Windows.Input.StylusPointCollection>. Dodaj nowo utworzone <xref:System.Windows.Ink.Stroke> do kolekcji <xref:System.Windows.Controls.InkPresenter.Strokes%2A> <xref:System.Windows.Controls.InkPresenter> i wydania pióra.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Instrukcje: Włączanie wprowadzania danych przez formant przy użyciu myszy  
 Jeśli dodasz poprzedni formant do aplikacji, uruchomisz go i użyjesz myszy jako urządzenia wejściowego, Zauważ, że pociągnięcia nie są utrwalane. Aby zachować pociągnięcia, gdy mysz jest używana jako urządzenie wejściowe, wykonaj następujące czynności:  
  
1. Zastąp <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> i Utwórz nowy <xref:System.Windows.Input.StylusPointCollection> Pobierz pozycję myszy po wystąpieniu zdarzenia i Utwórz <xref:System.Windows.Input.StylusPoint> przy użyciu danych punktu i Dodaj <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Zastąp metodę <xref:System.Windows.UIElement.OnMouseMove%2A>. Pobierz pozycję myszy po wystąpieniu zdarzenia i Utwórz <xref:System.Windows.Input.StylusPoint> przy użyciu danych z punktu.  Dodaj <xref:System.Windows.Input.StylusPoint> do obiektu <xref:System.Windows.Input.StylusPointCollection> utworzonego wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Zastąp metodę <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Utwórz nową <xref:System.Windows.Ink.Stroke> z danymi <xref:System.Windows.Input.StylusPointCollection> i Dodaj nową <xref:System.Windows.Ink.Stroke> utworzoną do kolekcji <xref:System.Windows.Controls.InkPresenter.Strokes%2A> <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Umieszczanie ich razem  
 Poniższy przykład jest formantem niestandardowym, który zbiera pismo odręczne, gdy użytkownik korzysta z myszy lub pióra.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Korzystanie z dodatkowych wtyczek i DynamicRenderers  
 Podobnie jak w przypadku InkCanvas, kontrolka niestandardowa może mieć niestandardowe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i dodatkowe obiekty <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Dodaj je do kolekcji <xref:System.Windows.UIElement.StylusPlugIns%2A>. Kolejność <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> obiektów w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> ma wpływ na wygląd atramentu, gdy jest renderowany. Załóżmy, że masz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> o nazwie `dynamicRenderer` i niestandardowej <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> o nazwie `translatePlugin`, która przesuwa atrament z pióra rysownicy. Jeśli `translatePlugin` jest pierwszym <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>i `dynamicRenderer` jest drugim, atrament "przepływy" będzie przesunięty w miarę przesuwania pióra przez użytkownika. Jeśli `dynamicRenderer` jest pierwszy i `translatePlugin` jest sekunda, atrament nie zostanie przesunięty do momentu wypróbowania pióra przez użytkownika.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Podsumowanie  
 Można utworzyć formant, który zbiera i renderuje atrament, zastępując metody zdarzeń pióra. Tworząc własny formant, wyprowadzając własne klasy <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i wstawiając je do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, można zaimplementować praktycznie każde zachowanie z możliwością rozdzielenia cyfrowym atramentem. Masz dostęp do danych <xref:System.Windows.Input.StylusPoint> w miarę ich generowania, co daje możliwość dostosowania <xref:System.Windows.Input.Stylus> danych wejściowych i renderowania na ekranie, zgodnie z potrzebami aplikacji. Ponieważ masz taki dostęp do danych <xref:System.Windows.Input.StylusPoint>, możesz zaimplementować kolekcję farb i renderować ją z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowana obsługa pisma odręcznego](advanced-ink-handling.md)
- [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
