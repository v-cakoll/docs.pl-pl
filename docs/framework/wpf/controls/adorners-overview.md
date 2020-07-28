---
title: Przegląd Moduły indeksowania układu
description: Dowiedz się więcej na temat Windows Presentation Foundation modułów definiowania układu, specjalnego typu FrameworkElement, który udostępnia podpowiedzi użytkownikowi, takie jak uchwyty funkcjonalne dla elementów.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167738"
---
# <a name="adorners-overview"></a>Przegląd Moduły indeksowania układu

Moduły definiowania układu są specjalnym typem <xref:System.Windows.FrameworkElement> , używanym do udostępniania wizualnych podpowiedzi użytkownikowi. Do innych celów, moduły definiowania układu mogą służyć do dodawania dojścia funkcjonalne do elementów lub dostarczania informacji o stanie dla formantu.

## <a name="about-adorners"></a>Moduły definiowania układu — informacje

<xref:System.Windows.Documents.Adorner>Jest to niestandardowa <xref:System.Windows.FrameworkElement> , która jest powiązana z <xref:System.Windows.UIElement> . Moduły definiowania układu są renderowane w <xref:System.Windows.Documents.AdornerLayer> , która jest powierzchnią renderowania, która zawsze znajduje się na wierzchu elementu, lub kolekcji elementów z elementami. Renderowanie modułu definiowania układu jest niezależne od renderowania <xref:System.Windows.UIElement> , z którym jest powiązany moduł definiowania układu. Moduł definiowania układu jest zwykle umieszczony względem elementu, z którym jest powiązany, za pomocą standardowego punktu początkowego współrzędnych 2D w lewym górnym rogu elementu.

Typowe aplikacje dla modułów definiowania układu obejmują:

- Dodanie dojść funkcjonalnych do obiektu <xref:System.Windows.UIElement> , który umożliwia użytkownikowi manipulowanie elementem w jakiś sposób (zmiana rozmiaru, obracanie, zmianę położenia itp.).
- Zapewnij wizualną opinię wskazującą różne stany lub w odpowiedzi na różne zdarzenia.
- Nałóż dekoracyjne elementy wizualne na <xref:System.Windows.UIElement> .
- Wizualnie Maskuj lub Przesłoń część lub wszystkie <xref:System.Windows.UIElement> .

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia podstawową strukturę służącą do definiowania elementów wizualnych. W poniższej tabeli wymieniono typy podstawowe używane podczas tworzenia obiektów i ich przeznaczenia. Poniżej przedstawiono kilka przykładów użycia:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Abstrakcyjna klasa bazowa, z której są dziedziczone wszystkie konkretne implementacje modułu definiowania układu.|
|<xref:System.Windows.Documents.AdornerLayer>|Klasa reprezentująca warstwę renderowania dla modułów definiowania układu dla co najmniej jednego elementu z.|
|<xref:System.Windows.Documents.AdornerDecorator>|Klasa, która umożliwia skojarzenie warstwy modułu definiowania układu z kolekcją elementów.|

## <a name="implementing-a-custom-adorner"></a>Implementowanie niestandardowego modułu definiowania układu

Struktura modułów definiowania układu dostarczana przez program [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest przeznaczona głównie do obsługi tworzenia niestandardowych modułów definiowania. Niestandardowy moduł definiowania układu jest tworzony przez implementację klasy, która dziedziczy z klasy abstrakcyjnej <xref:System.Windows.Documents.Adorner> .

> [!NOTE]
> Elementem nadrzędnym elementu <xref:System.Windows.Documents.Adorner> jest <xref:System.Windows.Documents.AdornerLayer> renderowanie, a <xref:System.Windows.Documents.Adorner> nie element, który jest tworzony.

Poniższy przykład przedstawia klasę implementującą prosty moduł definiowania układu. Przykładowy moduł definiowania układu po prostu tworzy rogi <xref:System.Windows.UIElement> z okręgów.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Na poniższej ilustracji przedstawiono SimpleCircleAdorner zastosowany do <xref:System.Windows.Controls.TextBox> :

![Zrzut ekranu pokazujący pole tekstowe z tekstem.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Zachowanie renderowania dla modułów definiowania układu

Należy zauważyć, że moduły definiowania układu nie uwzględniają nieodłącznego zachowania renderowania; upewnienie się, że moduł definiowania układu jest odpowiedzialny za implementację modułu definiowania układu. Typowym sposobem implementacji zachowania renderowania jest zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody i użycie jednego lub większej liczby <xref:System.Windows.Media.DrawingContext> obiektów w celu renderowania wizualizacji modułu definiowania układu w miarę potrzeb (jak pokazano w powyższym przykładzie).

> [!NOTE]
> Wszystkie elementy umieszczone w warstwie modułu definiowania układu są renderowane na podstawie pozostałych ustawionych stylów. Innymi słowy, moduły definiowania układu zawsze są widoczne na górze i nie mogą zostać zastąpione przy użyciu kolejności z.

## <a name="events-and-hit-testing"></a>Testy zdarzeń i trafień

Moduły definiowania układu odbierają zdarzenia wejściowe w taki sam sposób jak inne <xref:System.Windows.FrameworkElement> .  Ze względu na to, że moduł definiowania układu zawsze ma wyższy porządek osi z niż element, który jest w jego obszarze, moduł definiowania układu odbiera zdarzenia wejściowe (takie jak <xref:System.Windows.UIElement.Drop> lub <xref:System.Windows.UIElement.MouseMove> ), które mogą być przeznaczone dla bazowego elementu.  Moduł definiowania układu może nasłuchiwać określonych zdarzeń wejściowych i przekazać je do podstawowego elementu z własnym elementem, przez ponowne podnoszenie poziomu zdarzenia.

Aby włączyć przekazywanie testów trafień elementów pod modułem definiowania układu, ustaw właściwość test trafień na <xref:System.Windows.UIElement.IsHitTestVisible%2A> **false** w programie definiowania układu.  Aby uzyskać więcej informacji na temat testowania trafień, zobacz [test trafień w warstwie wizualnej](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Określanie układu pojedynczego elementu UIElement

Aby powiązać moduł definiowania układu z konkretną <xref:System.Windows.UIElement> , wykonaj następujące kroki:

1. Wywołaj metodę statyczną, <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Aby uzyskać <xref:System.Windows.Documents.AdornerLayer> obiekt dla elementu <xref:System.Windows.UIElement> do. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>wyszukuje drzewo wizualne, rozpoczynając od określonego <xref:System.Windows.UIElement> i zwraca początkową warstwę modułu definiowania układu. (Jeśli nie zostaną znalezione żadne warstwy modułu definiowania układu, metoda zwróci wartość null).

2. Wywołaj <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z elementem docelowym <xref:System.Windows.UIElement> .

 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej) z <xref:System.Windows.Controls.TextBox> nazwanym obiektem *TextBox*:

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Używanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do powiązania modułu definiowania układu z innym elementem nie jest obecnie obsługiwane.

## <a name="adorning-the-children-of-a-panel"></a>Określanie układu elementów podrzędnych panelu

Aby powiązać moduł definiowania układu z elementami podrzędnymi programu <xref:System.Windows.Controls.Panel> , wykonaj następujące kroki:

1. Wywołaj `static` metodę, <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Aby znaleźć warstwę modułu definiowania układu dla elementu, którego elementy podrzędne mają być podłączane.

2. Wylicz elementy podrzędne elementu nadrzędnego i Wywołaj metodę, <xref:System.Windows.Documents.AdornerLayer.Add%2A> Aby powiązać moduł definiowania układu z każdym elementem podrzędnym.

Poniższy przykład wiąże element SimpleCircleAdorner (pokazany powyżej) z elementem podrzędnym <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Przegląd Kształty i podstawowe rysowanie w WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie obrazami, rysowaniem i Visual](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Przegląd Rysowanie obiektów](../graphics-multimedia/drawing-objects-overview.md)
- [— Tematy porad](adorners-how-to-topics.md)
