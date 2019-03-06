---
title: Przegląd Moduły indeksowania układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 9c9d77c9771fd8759530267bd38cb7c0bb59598c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357953"
---
# <a name="adorners-overview"></a>Przegląd Moduły indeksowania układu
Moduły definiowania układu są specjalnym typem <xref:System.Windows.FrameworkElement>, który jest używany w celu zapewnienia podpowiedzi wizualne dla użytkownika. Wśród innych zastosowań moduły definiowania układu może służyć do dodawania funkcjonalności dojść do elementów lub podaj informacje o kontrolce stanie.  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>Moduły indeksowania układu — informacje  
 <xref:System.Windows.Documents.Adorner> Jest niestandardowy <xref:System.Windows.FrameworkElement> , jest powiązany z <xref:System.Windows.UIElement>. Moduły indeksowania układu — zostaną zrenderowane w <xref:System.Windows.Documents.AdornerLayer>, czyli powierzchnię renderowania, który jest zawsze na górze elementu element lub kolekcję elementów element. Renderowanie moduł definiowania układu jest niezależny od renderowanie <xref:System.Windows.UIElement> powiązaną moduł definiowania układu. Moduł definiowania układu zwykle znajduje się względem elementu, do którego jest powiązany, przy użyciu standardowego źródła współrzędnych 2-D, znajduje się w lewym górnym rogu elementu element.  
  
 Typowe dla modułów definiowania układu zastosowań:  
  
-   Dodawanie funkcjonalności dojścia do <xref:System.Windows.UIElement> , dzięki którym użytkownika do manipulowania elementem w jakiś sposób (zmiana rozmiaru, obracanie, zmiana położenia itp.).  
  
-   Przekazać wizualną opinię, aby wskazać różne stany, lub w odpowiedzi na różne zdarzenia.  
  
-   Nakładki visual dekoracje na <xref:System.Windows.UIElement>.  
  
-   Wizualnie maska lub zastąpić część lub całość <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia podstawowe struktury adorning elementów wizualnych. W poniższej tabeli wymieniono podstawowe typy używane podczas adorning obiektów i ich przeznaczenie. Wykonaj kilka przykładów użycia.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Abstrakcyjna klasa bazowa, z którego dziedziczą wszystkie implementacji konkretnego modułu definiowania układu kodu.|  
|<xref:System.Windows.Documents.AdornerLayer>|Klasa reprezentująca warstwy renderowania dla adorner(s) elementów co najmniej jeden element.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Klasa, która umożliwia warstwy moduł definiowania układu kodu ma zostać skojarzony z kolekcją elementów.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implementowanie niestandardowego modułu definiowania układu kodu  
 Dostarczone przez platformę moduły definiowania układu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest przeznaczony głównie do obsługi tworzenia niestandardowych modułów definiowania układu. Niestandardowy moduł definiowania układu, w której jest tworzona poprzez implementację klasy, która dziedziczy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.  
  
> [!NOTE]
>  Element nadrzędny <xref:System.Windows.Documents.Adorner> jest <xref:System.Windows.Documents.AdornerLayer> która renderuje <xref:System.Windows.Documents.Adorner>, nie jest powiązany element.  
  
 Poniższy przykład przedstawia klasę, która implementuje prosty moduł definiowania układu kodu. Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> przy użyciu kółka.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 Na poniższej ilustracji przedstawiono SimpleCircleAdorner dotyczą <xref:System.Windows.Controls.TextBox>.  
  
 ![Przykład moduły definiowania układu: Pole tekstowe ze zdefiniowanym](./media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Zachowanie renderowania dla modułów definiowania układu  
 Ważne jest, aby należy pamiętać, moduły definiowania układu nie ma żadnych zachowań nieprzerwaną pracę renderowania; zapewnienie, że moduł definiowania układu renderuje spoczywa implementujący moduł definiowania układu kodu.   Często stosowaną metodą wdrażania zachowanie renderowania jest zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody i używać co najmniej jednej <xref:System.Windows.Media.DrawingContext> obiekty do renderowania moduł definiowania układu wizualizacji, zgodnie z potrzebami (jak pokazano w powyższym przykładzie).  
  
> [!NOTE]
>  Cokolwiek umieszczone w warstwie moduł definiowania układu kodu jest renderowany na podstawie pozostałą część wszystkie style, które zostały ustawione. Innymi słowy moduły definiowania układu są zawsze wizualnie u góry i nie można zastąpić przy użyciu porządku osi z.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Zdarzenia i testowania trafień  
 Moduły definiowania układu odbierania zdarzeń wejściowych, podobnie jak każdy inny <xref:System.Windows.FrameworkElement>.  Ponieważ moduł definiowania układu ma zawsze wyższy porządku niż element go adorns, moduł definiowania układu odbiera zdarzenia wejściowe (takie jak <xref:System.Windows.UIElement.Drop> lub <xref:System.Windows.UIElement.MouseMove>) mogą być przeznaczone dla podstawowych powiązany element.  Moduł definiowania układu można wykrywać niektórych zdarzeń wejściowych i przekazać je do podstawowego elementu ze zdefiniowanym przez ponownego zgłaszania zdarzenia.  
  
 Aby włączyć, przekazywanego testowania trafień elementów w ramach modułu definiowania układu, należy ustawić testu trafienia <xref:System.Windows.UIElement.IsHitTestVisible%2A> właściwości **false** na moduł definiowania układu.  Aby uzyskać więcej informacji na temat testowania trafień zobacz  
  
 [Test trafienia w warstwie Visual](../graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Adorning pojedynczy element interfejsu użytkownika  
 Aby powiązać moduł definiowania układu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:  
  
1.  Wywołanie metody statycznej <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można pobrać <xref:System.Windows.Documents.AdornerLayer> dla obiektu <xref:System.Windows.UIElement> do być powiązany. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> przeprowadza górę drzewa wizualnego, rozpoczynając od określonego <xref:System.Windows.UIElement>i zwraca pierwszą warstwą moduł definiowania układu kodu znajdzie. (Jeśli nie warstwy moduł definiowania układu kodu nie zostaną znalezione, metoda zwraca wartość null.)  
  
2.  Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z obiektem docelowym <xref:System.Windows.UIElement>.  
  
 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać moduł definiowania układu z innego elementu nie jest obecnie obsługiwane.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Adorning elementy podrzędne panelu  
 Aby powiązać moduł definiowania układu z elementami podrzędnymi <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:  
  
1.  Wywołaj `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> można odnaleźć warstwy moduł definiowania układu dla elementu, którego elementy podrzędne, które mają być powiązany.  
  
2.  Wyliczyć elementy podrzędne elementu nadrzędnego, a wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z każdego elementu podrzędnego.  
  
 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), z elementami podrzędnymi <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.AdornerHitTestResult>
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Rysowanie obiektów — przegląd](../graphics-multimedia/drawing-objects-overview.md)
- [Tematy z instrukcjami](adorners-how-to-topics.md)
