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
ms.openlocfilehash: b3dc71182b7553a429bb17e1888a4108ceb3e286
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-ink-input-control"></a>Tworzenie formantu danych wejściowych atramentu
Można utworzyć niestandardowego formantu który dynamicznie i statycznie renderuje pismo odręczne. Oznacza to renderowania odręczne, jak użytkownik rysuje pociągnięcia, powodując pismo odręczne się pojawiać, aby "przebiegu" z pióra i wyświetlić odręczne po nim jest dodawana do kontrolki, albo za pomocą pióra wklejonych ze Schowka lub załadować z pliku. Aby dynamicznie renderowane odręczne, musisz użyć formantu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Statycznie renderowanie odręczne, konieczne jest przesłonięcie metody zdarzeń pióra (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, i <xref:System.Windows.UIElement.OnStylusUp%2A>) do zbierania <xref:System.Windows.Input.StylusPoint> danych, Utwórz pociągnięć i dodaj je do <xref:System.Windows.Controls.InkPresenter> (która renderuje pismo odręczne na formancie).  
  
 Ten temat zawiera następujące podsekcje:  
  
-   [Porady: zbieranie danych punktu Pióro i utworzyć pociągnięć odręcznych](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Porady: kontrola akceptowanie danych wejściowych z myszą](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Zestawienie go](#PuttingItTogether)  
  
-   [Przy użyciu dodatkowych dodatków plug-in i DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Zawierania](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Porady: zbieranie danych punktu Pióro i utworzyć pociągnięć odręcznych  
 Można utworzyć formantu, który zbiera i zarządza pisma odręcznego pociągnięć wykonaj następujące czynności:  
  
1.  Klasa wyprowadzona z <xref:System.Windows.Controls.Control> lub jednej z klas pochodnych <xref:System.Windows.Controls.Control>, takich jak <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Dodaj <xref:System.Windows.Controls.InkPresenter> klasy i zestawu <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości do nowego <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Dołącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkPresenter> przez wywołanie metody <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> metody i Dodaj <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Dzięki temu <xref:System.Windows.Controls.InkPresenter> do wyświetlania pismo odręczne, jak pióra punktu danych zbieranych przez formant.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Zastąpienie <xref:System.Windows.UIElement.OnStylusDown%2A> metody.  W przypadku tej metody Przechwytywanie pióra wywołaniem <xref:System.Windows.Input.Stylus.Capture%2A>. Przez Przechwytywanie pióra, formantu będzie w dalszym ciągu otrzymywać <xref:System.Windows.UIElement.StylusMove> i <xref:System.Windows.UIElement.StylusUp> zdarzeń nawet wtedy, gdy pióro pozostawia granice formantu. Nie jest ściśle wymagane, ale prawie zawsze odpowiednią dla uzyskać komfortowe środowisko użytkownika. Utwórz nową <xref:System.Windows.Input.StylusPointCollection> zbieranie <xref:System.Windows.Input.StylusPoint> danych. Na koniec należy dodać początkowego zestawu <xref:System.Windows.Input.StylusPoint> danych <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Zastąpienie <xref:System.Windows.UIElement.OnStylusMove%2A> — metoda i Dodaj <xref:System.Windows.Input.StylusPoint> danych <xref:System.Windows.Input.StylusPointCollection> obiektu, który został utworzony wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Zastąpienie <xref:System.Windows.UIElement.OnStylusUp%2A> — metoda i utworzyć nową <xref:System.Windows.Ink.Stroke> z <xref:System.Windows.Input.StylusPointCollection> danych. Dodaj nowe <xref:System.Windows.Ink.Stroke> utworzonego do <xref:System.Windows.Controls.InkPresenter.Strokes%2A> Kolekcja <xref:System.Windows.Controls.InkPresenter> i wersji Przechwytywanie pióra.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Porady: kontrola akceptowanie danych wejściowych z myszą  
 Dodawanie poprzedniego formantu do aplikacji, uruchom go i za pomocą myszy jako urządzenia wejściowego można zauważyć naciśnięcia nie są zachowywane. Aby zachować pociągnięć, gdy wskaźnik myszy jest używana jako urządzenia wejściowego, wykonaj następujące czynności:  
  
1.  Zastąpienie <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> i utworzyć nową <xref:System.Windows.Input.StylusPointCollection> Pobierz położenie myszy po wystąpieniu zdarzenia i utworzyć <xref:System.Windows.Input.StylusPoint> przy użyciu punktu danych i Dodaj <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Zastąpienie <xref:System.Windows.UIElement.OnMouseMove%2A> metody. Pobierz położenie myszy po wystąpieniu zdarzenia i utworzyć <xref:System.Windows.Input.StylusPoint> przy użyciu punktu danych.  Dodaj <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection> obiektu, który został utworzony wcześniej.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Zastąpienie <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  Utwórz nową <xref:System.Windows.Ink.Stroke> z <xref:System.Windows.Input.StylusPointCollection> danych i Dodaj nowe <xref:System.Windows.Ink.Stroke> utworzonego do <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekcji <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Zestawienie go  
 Poniższy przykład jest kontrolki niestandardowej, która zbiera pismo odręczne, gdy użytkownik używa myszy lub pióra.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Przy użyciu dodatkowych dodatków plug-in i DynamicRenderers  
 Podobnie jak przez obiekt InkCanvas formantu niestandardowego może mieć niestandardowej <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i dodatkowe <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obiektów. Dodaj je do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Kolejność <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> obiekty w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> ma wpływ na wygląd pisma odręcznego, gdy jest on renderowany. Załóżmy, że masz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> o nazwie `dynamicRenderer` i niestandardowej <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> o nazwie `translatePlugin` który przesuwa pismo odręczne z pióra. Jeśli `translatePlugin` jest pierwszy <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> w <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, i `dynamicRenderer` jest druga, gdy użytkownik przechodzi pióro zostanie przesunięty pismo odręczne przepływającego "". Jeśli `dynamicRenderer` jest najpierw i `translatePlugin` jest druga, pismo odręczne nie zostanie przesunięty, dopóki użytkownik podnosi pióra.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Można utworzyć formantu, który zbiera i renderuje pismo odręczne przez zastąpienie metody zdarzeń pióra. Tworząc własne kontrolki wyprowadzanie własne <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> klas i wstawianie ich do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, można zaimplementować praktycznie dowolne zachowanie imaginable odręczne cyfrowego. Masz dostęp do <xref:System.Windows.Input.StylusPoint> danych, ponieważ jest generowany, umożliwiając dostosować <xref:System.Windows.Input.Stylus> argument wejściowy i renderować ją na ekranie zależnie od potrzeb aplikacji. Ponieważ taki dostęp niskiego poziomu do <xref:System.Windows.Input.StylusPoint> danych, można zaimplementować odręczne kolekcji i renderować ją z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowana obsługa pisma odręcznego](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Uzyskiwanie dostępu i operowanie nimi piórem](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
