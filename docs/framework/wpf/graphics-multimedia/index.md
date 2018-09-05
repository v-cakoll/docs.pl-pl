---
title: Grafika i multimedia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: c7cae5be1d7e52186752d67354927084d118beb9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559014"
---
# <a name="graphics-and-multimedia"></a>Grafika i multimedia
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia obsługę multimedia, grafiki wektorowej, animacji i kompozycji zawartości, dzięki czemu deweloperzy mogą tworzyć interesujące interfejsy użytkownika i zawartości. Za pomocą [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], możesz utworzyć grafiki wektorowej lub złożonych animacji i zintegrować nośnika ze swoimi aplikacjami.  
  
 W tym temacie przedstawiono funkcje grafiki, animacji i media [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które umożliwiają dodawanie do aplikacji grafiki, efekty przejścia, dźwiękowe i wideo.  
  
> [!NOTE]
>  Używanie typów WPF w usłudze Windows jest zdecydowanie odradzane. Jeśli spróbujesz użyć typów WPF w usłudze Windows, usługa może nie działać zgodnie z oczekiwaniami.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Nowości dotyczące grafika i Multimedia w programie WPF 4  
 Kilka zmian dokonano powiązane grafiki i animacje.  
  
-   Zaokrąglanie układu  
  
     Podczas krawędzi obiektu mieści się w środku pikseli urządzenia, niezależnie od rozdzielczości DPI systemu grafiki można utworzyć renderowania artefaktów, takich jak krawędzie rozmyty lub półprzezroczystym. Poprzednie wersje WPF uwzględnione, ułatwią obsługę tego przypadku przyciąganie do pikseli. Silverlight 2 wprowadzono zaokrąglanie układ, który jest inny sposób Przenieś elementy znajdują się w granicach całego pikseli. WPF obsługuje teraz układ zaokrąglania z <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> dołączona właściwość na <xref:System.Windows.FrameworkElement>.  
  
-   Skład pamięci podręcznej  
  
     Za pomocą nowego <xref:System.Windows.Media.BitmapCache> i <xref:System.Windows.Media.BitmapCacheBrush> klasy, można złożoną częścią drzewa wizualnego jako mapę bitową w pamięci podręcznej i znacznie zwiększyć czas renderowania. Mapa bitowa reaguje na dane wejściowe użytkownika, takie jak kliknięcie myszą, i można malować na inne elementy, podobnie jak wszelkie pędzla.  
  
-   Obsługa programu do cieniowania 3 pikseli  
  
     WPF 4 kompilacje w górnej części <xref:System.Windows.Media.Effects.ShaderEffect> pomocy technicznej, wprowadzona w programie WPF 3.5 z dodatkiem SP1, umożliwiając aplikacjom zapisać efekty przy użyciu programu do cieniowania pikseli (PS) w wersji 3.0. Model programu do cieniowania PS 3.0 jest bardziej zaawansowane niż PS w wersji 2.0, co pozwala uzyskać jeszcze więcej efektów dotyczące obsługiwanego sprzętu.  
  
-   Zwalnianie funkcji  
  
     Możesz zwiększyć animacji przy użyciu funkcji sterowania tempem zmian, które zapewniają dodatkową kontrolę nad zachowaniem animacji. Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby zapewnić zachowanie o zmiennym rozmiarze animacji. Aby uzyskać więcej informacji, zobacz Typy sterowania tempem zmian w <xref:System.Windows.Media.Animation> przestrzeni nazw.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Grafika i renderowanie  
 WPF obsługuje wysokiej jakości grafika 2-D. Funkcje obejmują pędzle, geometrii, obrazy, kształty i przekształcenia. Aby uzyskać więcej informacji, zobacz [grafiki](../../../../docs/framework/wpf/graphics-multimedia/graphics.md). Renderowanie elementów graficznych opiera się na <xref:System.Windows.Media.Visual> klasy. Struktura obiektów wizualnych na ekranie jest opisana przez drzewo wizualne. Aby uzyskać więcej informacji, zobacz [Przegląd Renderowanie grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>Kształty 2-D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera bibliotekę często używane, rysowania wektor [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] kształtów, takich jak prostokąty i wielokropek, co pokazano na poniższej ilustracji.  
  
 ![Wielokropki i prostokąty](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Te wewnętrzne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kształty nie są po prostu kształtów: są elementy programowalne, które zaimplementować wiele funkcji, których można oczekiwać od najczęstsze formanty, które obejmują klawiatury i myszy. Poniższy przykład pokazuje, jak obsługiwać <xref:System.Windows.UIElement.MouseUp> Zdarzenie wywoływane, klikając <xref:System.Windows.Shapes.Ellipse> elementu.  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  x:Class="Window1" >  
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />  
</Window>  
```  
  
```csharp  
public partial class Window1  : Window  
{  
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)  
    {  
        MessageBox.Show("You clicked the ellipse!");  
    }  
}  
```  
  
```vb  
Partial Public Class Window1  
    Inherits Window  
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)  
        MessageBox.Show("You clicked the ellipse!")  
    End Sub  
End Class  
```  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe dla poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i związane z kodem.  
  
 ![Okno z tekstem "kliknięto przycisk wielokropka&#33;"](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Aby uzyskać więcej informacji, zobacz [kształty i podstawowe Rysowanie w WPF — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md). Wprowadzający przykład znaleźć w artykule [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>2-D geometrii  
 Gdy [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] kształty, które [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera nie są wystarczające, można użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Obsługa geometrii i ścieżki, aby utworzyć własny. Poniższa ilustracja przedstawia, jak używać geometrii do tworzenia kształtów, jako pędzla do rysowania i kiedy należy przyciąć innych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów.  
  
 ![Różne przypadki użycia ścieżki](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd Geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md). Wprowadzający przykład znaleźć w artykule [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>Efekty 2-D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera bibliotekę [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] klasy, których można tworzyć różne efekty. [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Możliwości renderowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, które mają gradientów, mapy bitowe, rysunki i wideo; i manipulować nimi przy użyciu obrotu, skalowanie i pochylanie. Na poniższej ilustracji przedstawiono przykładowy wiele efekty, można osiągnąć za pomocą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Pędzle.  
  
 ![Ilustracja różnych pędzli](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Aby uzyskać więcej informacji, zobacz [pędzle WPF — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md). Wprowadzający przykład znaleźć w artykule [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>Renderowanie 3-D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawiera zestaw [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] możliwości renderowania, które integrują się z [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obsługi grafiki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w kolejności, w celu utworzenia bardziej atrakcyjne układ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]i wizualizacja danych. Na jednym końcu spektrum [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia renderowanie [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazów na powierzchni [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] kształty, które przedstawiono na poniższej ilustracji.  
  
 ![Zrzut ekranu przedstawiający przykładowy przykład Visual3D](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd grafiki 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md). Wprowadzający przykład znaleźć w artykule [3-przykładowe stałych](https://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animacja  
 Użyj animacji, formantów i elementów, rozwoju, potrząsanie, uruchamiaj i zanikanie; i tworzyć interesujące przejścia stron i inne. Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia, aby animować większość właściwości i nie tylko można animować większość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obiekty, można również użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animować niestandardowe obiekty, które tworzysz.  
  
 ![Obrazy modułu animowany](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Wprowadzający przykład znaleźć w artykule [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Nośnik  
 Obrazy, wideo i audio są bogatych sposób przekazywania informacji i użytkownika.  
  
### <a name="images"></a>Obrazy  
 Obrazy, które obejmują ikony, tła i nawet części animacji, są podstawowym składnikiem większości aplikacji. Ponieważ często zachodzi potrzeba używania obrazów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia możliwość pracy z nimi w na różne sposoby. Poniższa ilustracja przedstawia tylko jeden z tych sposobów.  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd obrazowanie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="video-and-audio"></a>Audio i wideo  
 Funkcja podstawowe funkcje grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest zapewnienie natywnej obsługi do pracy z multimediami, w tym wideo i audio. Poniższy przykład pokazuje, jak można wstawić odtwarzacz multimediów do aplikacji.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> jest w stanie odtwarzanie dźwięku i wideo, a następnie rozszerzyć, aby umożliwić łatwe tworzenie niestandardowych [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd Multimedia](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Animacja i chronometraż](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Grafika 3-D](https://msdn.microsoft.com/library/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [Multimedia](https://msdn.microsoft.com/library/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
