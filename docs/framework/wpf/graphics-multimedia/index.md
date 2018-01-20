---
title: Grafika i multimedia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 013ae46e2d90a9eda42d33e95e590812489fa04b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="graphics-and-multimedia"></a>Grafika i multimedia
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia obsługę multimediów, grafiki wektorowej, animacji i zawartości kompozycji, dzięki czemu deweloperzy mogą tworzyć interesujące interfejsów użytkownika i zawartości. Przy użyciu [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], można utworzyć grafiki wektorowej lub złożonych animacji i integracji nośnika w aplikacji.  
  
 W tym temacie przedstawiono funkcje grafiki, animacji i multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które umożliwiają dodanie grafiki, efekty przejścia dźwięku i wideo do aplikacji.  
  
> [!NOTE]
>  Używanie typów WPF w usłudze systemu Windows jest zalecane. Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługi mogą nie działać zgodnie z oczekiwaniami.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Nowości dotyczące grafiki i multimediów na platformie WPF 4  
 Kilka wprowadzono zmiany dotyczące grafiki i animacji.  
  
-   Zaokrąglanie układu  
  
     Podczas krawędzi obiektu znajduje się w środku urządzenia pikseli, system grafiki niezależny od DPI można utworzyć renderowania artefaktów, takich jak rozmyte lub półprzezroczysty krawędzi. Poprzednie wersje WPF włączone przyciąganie pikseli, które dodatkowo ułatwią obsługę tego przypadku. Silverlight 2 wprowadzono zaokrąglania układu, sposób można przenosić elementy, dzięki czemu znajdują się na cały pikseli. WPF obsługuje teraz układu zaokrąglania z <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> dołączona właściwość <xref:System.Windows.FrameworkElement>.  
  
-   Kompozycja pamięci podręcznej  
  
     Przy użyciu nowej <xref:System.Windows.Media.BitmapCache> i <xref:System.Windows.Media.BitmapCacheBrush> klasy, można buforować złożonych częścią drzewa wizualnego jako mapę bitową i znacznie zwiększyć czas renderowania. Mapa bitowa reaguje na dane wejściowe użytkownika, takie jak kliknięcie myszą i malować na inne elementy, podobnie jak wszelkie pędzla.  
  
-   Obsługa 3 cieniowania pikseli  
  
     WPF 4 kompilacje nad <xref:System.Windows.Media.Effects.ShaderEffect> Obsługa wprowadzone w WPF 3.5 z dodatkiem SP1, umożliwiając aplikacjom zapisać efekty przy użyciu programu do cieniowania pikseli (PS) w wersji 3.0. Model programu do cieniowania PS 3.0 jest bardziej złożone niż PS 2.0, dzięki czemu jeszcze bardziej skutków dla obsługiwanego sprzętu.  
  
-   Zwalnianie funkcji  
  
     Można zwiększyć animacje z funkcji sterowania tempem zmian, które zapewniają dodatkową kontrolę nad zachowanie animacji. Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby zapewnić zachowanie o zmiennym rozmiarze animacji. Aby uzyskać więcej informacji, zobacz Typy sterowania tempem zmian w <xref:System.Windows.Media.Animation> przestrzeni nazw.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Grafika i renderowania  
 WPF obsługuje grafiki 2-D wysokiej jakości. Funkcje obejmują pędzle, mają geometrię, obrazy, kształty i przekształcenia. Aby uzyskać więcej informacji, zobacz [grafiki](../../../../docs/framework/wpf/graphics-multimedia/graphics.md). Renderowanie elementów graficznego opiera się na <xref:System.Windows.Media.Visual> klasy. Struktura obiektów visual na ekranie została opisana w drzewie wizualnym. Aby uzyskać więcej informacji, zobacz [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>Kształty 2-D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zawiera bibliotekę często używane, rysowane wektor [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] kształtów, takich jak prostokąty i wielokropek, które na poniższej ilustracji przedstawiono.  
  
 ![Wielokropki i prostokąty](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Te wewnętrzne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kształtów nie są po prostu kształtów: są programowalny elementy, które implementuje wiele funkcji, których można oczekiwać od najbardziej typowych formantów, które obejmują klawiatury i myszy. Poniższy przykład przedstawia sposób obsługi <xref:System.Windows.UIElement.MouseUp> Zdarzenie wywoływane po kliknięciu <xref:System.Windows.Shapes.Ellipse> elementu.  
  
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
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i związane z kodem.  
  
 ![Okno z tekstem "kliknięto przycisk wielokropka &33;" ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Aby uzyskać więcej informacji, zobacz [kształtów i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md). Dla przykładu wprowadzające, zobacz [przykładowe elementy kształtu](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>2-D mają geometrię  
 Gdy [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, który [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewnia nie są wystarczające, można użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługę mają geometrię i ścieżki do tworzenia własnych. Na poniższej ilustracji pokazano, jak używać mają geometrię Utwórz kształtów, jako pędzla do rysowania i obcina innych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów.  
  
 ![Różnych zastosowań ścieżki](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Aby uzyskać więcej informacji, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md). Dla przykładu wprowadzające, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>Efekty 2-D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zawiera bibliotekę [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] klasy, które umożliwia tworzenie wielu efektów. [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Możliwości renderowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów, które mają gradientów, mapy bitowe, rysunki i wideo; i manipulowania nimi przy użyciu obracanie, skalowanie i pochylanie. Na poniższej ilustracji przedstawiono przykładowy wiele efektów można osiągnąć za pomocą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Pędzle.  
  
 ![Ilustracja różnych pędzli](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Aby uzyskać więcej informacji, zobacz [omówienie pędzle WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md). Dla przykładu wprowadzające, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>Renderowanie 3-D  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zawiera zestaw [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] możliwości renderowania, które integrują się z [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obsługuje grafiki w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w kolejności do tworzenia układu ciekawsze [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]i wizualizacja danych. Na jednym końcu widma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia renderowanie [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obrazów na powierzchni [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] kształtów, co pokazano na poniższej ilustracji.  
  
 ![Zrzut ekranu przedstawiający przykładowy Visual3D](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Aby uzyskać więcej informacji, zobacz [3-Przegląd grafiki](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md). Dla przykładu wprowadzające, zobacz [3-próbki stałych](http://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animacja  
 Użyj animacji, aby wprowadzić formanty i elementy powiększania, potrząsanie pokrętła i stopniowe; i utwórz interesujące przejścia stron i inne. Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia do animowania właściwości większości, tylko nie można animować większość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obiekty, można również użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do animowania tworzonych obiektów.  
  
 ![Obrazy modułu animowany](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Dla przykładu wprowadzające, zobacz [galerii przykład animacji](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Nośnik  
 Obrazy, wideo i audio metodami bogatych przekazywania informacji i użytkownika.  
  
### <a name="images"></a>Obrazy  
 Obrazów, które obejmują ikony, tła i nawet części animacji, są częścią podstawowych większości aplikacji. Ponieważ często muszą używać obrazów, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia pracować z nimi w różny sposób. Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Aby uzyskać więcej informacji, zobacz [Imaging omówienie](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="video-and-audio"></a>Audio i wideo  
 Funkcja podstawowe możliwości grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest zapewnienie macierzystą obsługę do pracy z multimediów, w tym audio i wideo. Poniższy przykład pokazuje, jak można umieścić Windows media player w aplikacji.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement>ma możliwość odtwarzania audio i wideo i jest rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
 Aby uzyskać więcej informacji, zobacz [omówienie Multimedia](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Synchronizację](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [3-grafiki](http://msdn.microsoft.com/library/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [Multimedia](http://msdn.microsoft.com/library/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
