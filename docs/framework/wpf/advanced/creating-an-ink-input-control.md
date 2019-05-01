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
ms.openlocfilehash: 105a44f90c1c654a21fc8920a149ad63b2dabc99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928720"
---
# <a name="creating-an-ink-input-control"></a>Tworzenie formantu danych wejściowych atramentu
Można utworzyć formant niestandardowy, dynamicznie i statycznie renderowanie pisma odręcznego. Oznacza to renderowanie pisma odręcznego, jak użytkownik rysuje pociągnięcia, powodując pisma odręcznego się "flow" z pióra i wyświetlić pisma odręcznego po nim jest dodawany do kontroli, za pomocą pióra, wklejonych ze Schowka, albo załadować z pliku. Aby powodować dynamiczne renderowanie pisma odręcznego, musisz użyć kontrolki <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Statycznie renderowanie pisma odręcznego, konieczne jest przesłonięcie metody zdarzeń pióra (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, i <xref:System.Windows.UIElement.OnStylusUp%2A>) do zbierania <xref:System.Windows.Input.StylusPoint> dane, tworzyć pociągnięć i dodać je do <xref:System.Windows.Controls.InkPresenter> (która renderuje pismo odręczne na formancie).  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Instrukcje: Zbieranie danych punktu pióra i utworzyć pociągnięć odręcznych](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Instrukcje: Włączanie kontroli nad do przyjmowania danych wejściowych z myszy](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Umieszczenie go razem](#PuttingItTogether)  
  
- [Za pomocą dodatkowych dodatków plug-in i DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Podsumowanie](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Instrukcje: Zbieranie danych punktu pióra i utworzyć pociągnięć odręcznych  
 Aby utworzyć formant, który służy do zbierania i zarządza pisma odręcznego pociągnięć wykonaj następujące czynności:  
  
1. Wyprowadzić klasę z <xref:System.Windows.Controls.Control> lub jednej z klas pochodnych <xref:System.Windows.Controls.Control>, takich jak <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Dodaj <xref:System.Windows.Controls.InkPresenter> klasy i zestaw <xref:System.Windows.Controls.ContentControl.Content%2A> nową właściwość <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Dołącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkPresenter> przez wywołanie metody <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> metodę i Dodaj <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Dzięki temu <xref:System.Windows.Controls.InkPresenter> do wyświetlenia pismo odręczne, ponieważ dane punktu pióra są zbierane przez Twoją kontrolą.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Zastąp <xref:System.Windows.UIElement.OnStylusDown%2A> metody.  W przypadku tej metody Przechwytywanie pióra wywołaniem <xref:System.Windows.Input.Stylus.Capture%2A>. Przechwytując Pióro, będą nadal otrzymywać kontroli nad <xref:System.Windows.UIElement.StylusMove> i <xref:System.Windows.UIElement.StylusUp> zdarzenia, nawet jeśli opuszczeniu przez pióro granic formantu. Nie jest ściśle wymagane, ale prawie zawsze żądane środowisko pracy użytkownika. Utwórz nową <xref:System.Windows.Input.StylusPointCollection> zbieranie <xref:System.Windows.Input.StylusPoint> danych. Na koniec należy dodać początkowy zestaw <xref:System.Windows.Input.StylusPoint> danych <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Zastąpienie <xref:System.Windows.UIElement.OnStylusMove%2A> metody i Dodaj <xref:System.Windows.Input.StylusPoint> danych <xref:System.Windows.Input.StylusPointCollection> obiektu, który został utworzony wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Zastąp <xref:System.Windows.UIElement.OnStylusUp%2A> metody i Utwórz nowy <xref:System.Windows.Ink.Stroke> z <xref:System.Windows.Input.StylusPointCollection> danych. Dodaj nowy <xref:System.Windows.Ink.Stroke> zostanie utworzony w celu <xref:System.Windows.Controls.InkPresenter.Strokes%2A> zbiór <xref:System.Windows.Controls.InkPresenter> i zwolnij Przechwytywanie pióra.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Instrukcje: Włączanie kontroli nad do przyjmowania danych wejściowych z myszy  
 Dodaj poprzedni formant do aplikacji, uruchom go i wprowadzać dane za pomocą myszy można zauważyć pociągnięć nie są zachowywane. Aby zachować pociągnięć, gdy wskaźnik myszy jest używana jako urządzenia wejściowego, wykonaj następujące czynności:  
  
1. Zastąp <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> i Utwórz nowy <xref:System.Windows.Input.StylusPointCollection> uzyskiwanie położenie kursora myszy, gdy zdarzenie wystąpiło i tworzenie <xref:System.Windows.Input.StylusPoint> przy użyciu punktu danych, a następnie dodaj <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Zastąp <xref:System.Windows.UIElement.OnMouseMove%2A> metody. Pobierz położenie kursora myszy, gdy zdarzenie wystąpiło i Utwórz <xref:System.Windows.Input.StylusPoint> przy użyciu punktu danych.  Dodaj <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection> obiektu, który został utworzony wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Zastąp <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  Utwórz nową <xref:System.Windows.Ink.Stroke> z <xref:System.Windows.Input.StylusPointCollection> danych i Dodaj nowy <xref:System.Windows.Ink.Stroke> zostanie utworzony w celu <xref:System.Windows.Controls.InkPresenter.Strokes%2A> zbiór <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Umieszczenie go razem  
 Poniższy przykład jest formant niestandardowy, który zbiera pisma odręcznego, gdy użytkownik używa myszy lub pióra.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Za pomocą dodatkowych dodatków plug-in i DynamicRenderers  
 Np. przez obiekt InkCanvas niestandardową kontrolkę może mieć niestandardowe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> wraz z dodatkowymi <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obiektów. Dodaj je do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Kolejność <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> obiekty w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> ma wpływ na wygląd pisma odręcznego, gdy jest on renderowany. Załóżmy, że masz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> o nazwie `dynamicRenderer` i niestandardowego <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> o nazwie `translatePlugin` który przesuwa pisma odręcznego z pióra. Jeśli `translatePlugin` jest to pierwszy <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, i `dynamicRenderer` jest to druga pisma odręcznego "przepływy" spowoduje przesunięcie, gdy użytkownik przesuwa pióra. Jeśli `dynamicRenderer` jest pierwszym, i `translatePlugin` jest po drugie, pisma odręcznego nie spowoduje przesunięcie, dopóki użytkownik wind pióra.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Można utworzyć formant, który służy do zbierania i renderuje pismo odręczne poprzez zastąpienie metody zdarzeń pióra. Tworząc własne kontrolki, pochodząca własne <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> klasy i wstawiania ich do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, możesz wdrożyć niemal dowolne zachowanie imaginable z cyfrowy atrament. Masz dostęp do <xref:System.Windows.Input.StylusPoint> dane ponieważ jest generowany, dzięki czemu możesz dostosować <xref:System.Windows.Input.Stylus> danych wejściowych i renderować ją na ekranie jako odpowiedni dla aplikacji. Ponieważ masz takiego niskiego poziomu dostępu do <xref:System.Windows.Input.StylusPoint> danych, można zaimplementować kolekcji pisma odręcznego i renderować ją z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowana obsługa pisma odręcznego](advanced-ink-handling.md)
- [Uzyskiwania dostępu i manipulowania piórem](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
