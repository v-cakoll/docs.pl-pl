---
title: Przegląd Moduły indeksowania układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111182"
---
# <a name="adorners-overview"></a>Przegląd Moduły indeksowania układu

Adorners są specjalnym <xref:System.Windows.FrameworkElement>typem , używane do dostarczania wizualnych wskazówek dla użytkownika. Wśród innych zastosowań Adorners może służyć do dodawania uchwytów funkcjonalnych do elementów lub podać informacje o stanie formantu.

## <a name="about-adorners"></a>Więcej o: Adorners

Jest <xref:System.Windows.Documents.Adorner> to <xref:System.Windows.FrameworkElement> zwyczaj, który <xref:System.Windows.UIElement>jest powiązany z . Adorners są renderowane <xref:System.Windows.Documents.AdornerLayer>w programie , który jest powierzchnią renderowania, która jest zawsze na szczycie element zdobione lub kolekcji elementów zdobione. Renderowanie adorner jest niezależna od <xref:System.Windows.UIElement> renderowania, że adorner jest zobowiązany do. Adorner jest zazwyczaj umieszczony względem elementu, do którego jest powiązany, przy użyciu standardowego początku współrzędnych 2D znajduje się w lewym górnym rogu elementu zdobione.

Typowe zastosowania adorners obejmują:

- Dodawanie uchwytów funkcjonalnych <xref:System.Windows.UIElement> do, które umożliwiają użytkownikowi manipulowanie elementem w jakiś sposób (zmień rozmiar, obróć, zmień położenie itp.).
- Przekaż wizualne informacje zwrotne, aby wskazać różne stany lub w odpowiedzi na różne zdarzenia.
- Nakładaj dekoracje wizualne na . <xref:System.Windows.UIElement>
- Wizualnie maskować lub zastępować część <xref:System.Windows.UIElement>lub całość pliku .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia podstawową strukturę zdobiąc elementy wizualne. W poniższej tabeli wymieniono typy podstawowe używane podczas ozdabiania obiektów i ich przeznaczenie. Kilka przykładów użycia wykonaj następujące:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Abstrakcyjna klasa podstawowa, z której dziedziczą wszystkie implementacje adornera betonu.|
|<xref:System.Windows.Documents.AdornerLayer>|Klasa reprezentująca warstwę renderowania dla adorner(ów) jednego lub więcej elementów ozdobionych.|
|<xref:System.Windows.Documents.AdornerDecorator>|Klasa, która umożliwia adorner warstwy do skojarzenia z kolekcji elementów.|

## <a name="implementing-a-custom-adorner"></a>Implementowanie niestandardowego adornera

Adorners framework dostarczone [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przez ma na celu przede wszystkim do obsługi tworzenia niestandardowych adorners. Niestandardowy adorner jest tworzony przez implementowanie klasy, <xref:System.Windows.Documents.Adorner> która dziedziczy z klasy abstrakcyjnej.

> [!NOTE]
> Element nadrzędny <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> jest, który <xref:System.Windows.Documents.Adorner>renderuje , nie element jest zdobione.

W poniższym przykładzie pokazano klasy, która implementuje prosty adorner. Przykład adorner po prostu zdobi rogi <xref:System.Windows.UIElement> z okręgów.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Na poniższej ilustracji przedstawiono simplecircleAdorner zastosowane do <xref:System.Windows.Controls.TextBox>:

![Zrzut ekranu przedstawiający pole tekstowe z ozdobami.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Zachowanie renderowania dla Adorners

Należy pamiętać, że adorners nie zawierają żadnych nieodłączne zachowanie renderowania; zapewnienie, że adorner renderuje jest odpowiedzialny za implementator adorner. Typowym sposobem implementowania zachowania renderowania jest <xref:System.Windows.UIElement.OnRender%2A> zastąpienie metody i <xref:System.Windows.Media.DrawingContext> użycie jednego lub więcej obiektów do renderowania wizualizacji adorner w razie potrzeby (jak pokazano w powyższym przykładzie).

> [!NOTE]
> Wszystko, co znajduje się w warstwie adorner, jest renderowane na pozostałych ustawionych stylach. Innymi słowy adorners są zawsze wizualnie na górze i nie można zastąpić za pomocą z-order.

## <a name="events-and-hit-testing"></a>Testy zdarzeń i trafień

Adorners odbierać zdarzenia wejściowe, podobnie jak każdy inny <xref:System.Windows.FrameworkElement>.  Ponieważ adorner zawsze ma wyższy porządek z niż element, który zdobi, adorner <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove>odbiera zdarzenia wejściowe (takie jak lub ), które mogą być przeznaczone dla podstawowego elementu zdobionego.  Adorner można nasłuchiwać niektórych zdarzeń wejściowych i przekazać je do podstawowego element zdobione przez ponowne podnoszenie zdarzenia.

Aby włączyć pass-through testowania trafień elementów w <xref:System.Windows.UIElement.IsHitTestVisible%2A> adorner, ustaw właściwość testu trafienia **false** na adorner.  Aby uzyskać więcej informacji na temat testowania trafień, zobacz [Testowanie trafień w warstwie wizualnej](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Ozdabianie pojedynczego interfejsu użytkownika

Aby powiązać adorner <xref:System.Windows.UIElement>z określonym , wykonaj następujące kroki:

1. Wywołanie metody <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> statycznej, <xref:System.Windows.Documents.AdornerLayer> aby <xref:System.Windows.UIElement> uzyskać obiekt do zdobienia. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>przechodzi w górę drzewa wizualnego, zaczynając od określonego <xref:System.Windows.UIElement>programu i zwraca pierwszą warstwę adorner, która zostanie wynajęta. (Jeśli nie zostaną znalezione żadne warstwy adorner, metoda zwraca wartość null.)

2. Wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody, aby powiązać adorner do obiektu docelowego <xref:System.Windows.UIElement>.

 Poniższy przykład wiąże SimpleCircleAdorner (pokazano powyżej) o <xref:System.Windows.Controls.TextBox> nazwie *myTextBox:*

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind adorner to another element is currently not supported Using to bind an adorner to another element is currently not supported.

## <a name="adorning-the-children-of-a-panel"></a>Ozdabianie dzieci panelu

Aby powiązać adorner z <xref:System.Windows.Controls.Panel>elementami podrzędnymi , wykonaj następujące kroki:

1. Wywołanie `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody, aby znaleźć warstwę adorner dla elementu, którego elementy podrzędne mają być zdobione.

2. Wyliczyć za pośrednictwem elementów podrzędnych <xref:System.Windows.Documents.AdornerLayer.Add%2A> elementu nadrzędnego i wywołać metodę powiązania adorner do każdego elementu podrzędnego.

Poniższy przykład wiąże SimpleCircleAdorner (pokazano powyżej) do <xref:System.Windows.Controls.StackPanel> elementów podrzędnych o nazwie *myStackPanel:*

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Przegląd Kształty i podstawowe rysowanie w WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Przegląd Rysowanie obiektów](../graphics-multimedia/drawing-objects-overview.md)
- [Tematy in jakże](adorners-how-to-topics.md)
