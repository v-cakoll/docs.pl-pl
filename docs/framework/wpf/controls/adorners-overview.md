---
title: Przegląd Moduły indeksowania układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 6dd38b9e24b42de8945c0e9729f8f30cf901fc3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adorners-overview"></a>Przegląd Moduły indeksowania układu
Modułu definiowania układu kodu jest specjalnym rodzajem <xref:System.Windows.FrameworkElement>używane do zapewnienia wizualnych do użytkownika. Oprócz innych zastosowań modułu definiowania układu kodu może służyć do dodawania funkcjonalności dojść do elementów lub podaj informacje o formancie.  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>Temat definiowania układu  
 <xref:System.Windows.Documents.Adorner> Jest niestandardowy <xref:System.Windows.FrameworkElement> który jest powiązany <xref:System.Windows.UIElement>. Modułu definiowania układu kodu są renderowane w <xref:System.Windows.Documents.AdornerLayer>, czyli powierzchnię renderowania, który jest zawsze element element lub zbiór elementów ze zdefiniowanym. Renderowanie moduł definiowania układu jest niezależna od renderowanie <xref:System.Windows.UIElement> powiązaną moduł definiowania układu. Moduł definiowania układu zazwyczaj znajduje się względem elementu, do którego jest powiązany, przy użyciu standardowych 2-D zerowy znajduje się w lewym górnym ze zdefiniowanym elementu.  
  
 Typowe zastosowania do definiowania układu obejmują:  
  
-   Dodawanie funkcjonalności dojścia do <xref:System.Windows.UIElement> umożliwiających użytkownika do manipulowania elementem w jakiś sposób (zmiana rozmiaru, obracanie, zmiana położenia itp.).  
  
-   Wizualne, aby wskazać różne stany, lub w odpowiedzi na różne zdarzenia.  
  
-   Nakładki visual dekoracje na <xref:System.Windows.UIElement>.  
  
-   Wizualne zamaskować lub zastąpienie części lub całości <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia podstawową strukturę adorning elementów wizualnych. W poniższej tabeli wymieniono podstawowych typów używany, gdy adorning obiektów i ich przeznaczenie. Należy wykonać kilka przykładów użycia.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Abstrakcyjna klasa podstawowa, z której dziedziczy wszystkie implementacje konkretnego modułu definiowania układu kodu.|  
|<xref:System.Windows.Documents.AdornerLayer>|Klasa reprezentująca warstwy renderowania dla adorner(s) elementów co najmniej jeden element.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Klasa, która umożliwia warstwy modułu definiowania układu kodu ma zostać skojarzony z kolekcją elementów.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implementowanie niestandardowego modułu definiowania układu kodu  
 Dostarczone przez platformę modułu definiowania układu kodu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest przeznaczony głównie do obsługi tworzenia niestandardowych modułów definiowania układu. Niestandardowy moduł definiowania układu kodu jest tworzony przez implementującej klasy, która dziedziczy z klasy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.  
  
> [!NOTE]
>  Element nadrzędny <xref:System.Windows.Documents.Adorner> jest <xref:System.Windows.Documents.AdornerLayer> która renderuje <xref:System.Windows.Documents.Adorner>, nie jest adorned element.  
  
 Poniższy przykład przedstawia klasę zawierającą implementację prostego moduł definiowania układu kodu. Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> z okręgi.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Na poniższej ilustracji przedstawiono SimpleCircleAdorner stosowane do <xref:System.Windows.Controls.TextBox>.  
  
 ![Przykład definiowania układu: Pole tekstowe ze zdefiniowanym](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Sposób renderowania modułu definiowania układu kodu  
 Należy pamiętać, że modułu definiowania układu kodu nie zawierają żadnych zachowania związanego z używaniem renderowania; zapewnienie, że moduł definiowania układu renderuje jest odpowiedzialny za implementujący modułu definiowania układu kodu.   Jest to często stosowana metoda wdrażania sposób renderowania do przesłonięcia <xref:System.Windows.UIElement.OnRender%2A> — metoda i użyj co najmniej jeden <xref:System.Windows.Media.DrawingContext> obiekty do renderowania elementów wizualnych moduł definiowania układu, zgodnie z potrzebami (jak pokazano w powyższym przykładzie).  
  
> [!NOTE]
>  Niczego umieszczone w warstwie modułu definiowania układu kodu jest renderowany na górze reszty wszystkie style, które zostało ustawione. Innymi słowy modułu definiowania układu kodu są zawsze wizualnie u góry i nie można zastąpić przy użyciu porządek osi z.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Zdarzenia i testowania trafień  
 Definiowania układu odbierania zdarzeń wejściowych, podobnie jak każdy inny <xref:System.Windows.FrameworkElement>.  Moduł definiowania układu ma zawsze wyższe porządek od elementu go adorns, moduł definiowania układu odbiera zdarzenia wejściowe (takie jak <xref:System.Windows.UIElement.Drop> lub <xref:System.Windows.UIElement.MouseMove>) mogą być przeznaczone dla podstawowych adorned elementu.  Moduł definiowania układu można nasłuchiwać określone zdarzenia wejściowe i przekazać je do odpowiedniego elementu ze zdefiniowanym przez ponownego podniesienie zdarzenia.  
  
 Przekazujący testowania trafień elementów w obszarze moduł definiowania układu, ustaw testu trafienia <xref:System.Windows.UIElement.IsHitTestVisible%2A> właściwości **false** na moduł definiowania układu.  Aby uzyskać więcej informacji na temat testowania trafień zobacz  
  
 [Testowanie w warstwie Visual trafień](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Adorning pojedynczy element UIElement  
 Aby powiązać modułu definiowania układu kodu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:  
  
1.  Wywołanie metody statycznej <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> uzyskanie <xref:System.Windows.Documents.AdornerLayer> obiekt do <xref:System.Windows.UIElement> do można adorned. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> przedstawiono w górę drzewa wizualnego, rozpoczynając od określonego <xref:System.Windows.UIElement>i zwraca znajdzie pierwszą warstwę modułu definiowania układu kodu. (Jeśli nie zostaną znalezione nie warstwy modułu definiowania układu kodu, metoda zwraca wartość null.)  
  
2.  Wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu w miejscu docelowym <xref:System.Windows.UIElement>.  
  
 Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać modułu definiowania układu kodu do innego elementu nie jest obecnie obsługiwany.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Adorning elementy podrzędne panelu  
 Aby powiązać modułu definiowania układu kodu do elementów podrzędnych <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:  
  
1.  Wywołanie `static` metody <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można znaleźć warstwy modułu definiowania układu kodu dla elementu, którego elementy podrzędne mają być adorned.  
  
2.  Wyliczenia elementów podrzędnych elementu nadrzędnego i wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu do każdego elementu podrzędnego.  
  
 Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej) do elementów podrzędnych <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
