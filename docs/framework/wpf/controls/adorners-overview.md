---
title: Przegląd Moduły indeksowania układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 22d9b1eddbb6db47fb15deebf94cfc5f8d37a380
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040837"
---
# <a name="adorners-overview"></a>Przegląd Moduły indeksowania układu

Moduły definiowania układu są specjalnym typem <xref:System.Windows.FrameworkElement>, używanym do udostępniania wizualnych podpowiedzi użytkownikowi. Do innych celów, moduły definiowania układu mogą służyć do dodawania dojścia funkcjonalne do elementów lub dostarczania informacji o stanie dla formantu.

## <a name="about-adorners"></a>Moduły definiowania układu — informacje

<xref:System.Windows.Documents.Adorner> jest niestandardowym <xref:System.Windows.FrameworkElement>, który jest powiązany z <xref:System.Windows.UIElement>. Moduły definiowania układu są renderowane w <xref:System.Windows.Documents.AdornerLayer>, która jest powierzchnią renderowania, która zawsze znajduje się na wierzchu elementu, lub kolekcji elementów z elementami. Renderowanie modułu definiowania układu jest niezależne od renderowania <xref:System.Windows.UIElement>, z którym jest powiązany moduł definiowania układu. Moduł definiowania układu jest zwykle umieszczony względem elementu, z którym jest powiązany, przy użyciu standardowego punktu początkowego współrzędnych 2-D znajdującego się w lewym górnym rogu elementu.

Typowe aplikacje dla modułów definiowania układu obejmują:

- Dodanie dojść funkcjonalnych do <xref:System.Windows.UIElement>, które umożliwiają użytkownikowi manipulowanie elementem w jakiś sposób (zmiana rozmiaru, obracanie, zmiana położenia itp.).
- Zapewnij wizualną opinię wskazującą różne stany lub w odpowiedzi na różne zdarzenia.
- Nałóż dekoracje wizualizacji na <xref:System.Windows.UIElement>.
- Wizualnie Maskuj lub Przesłoń część lub wszystkie <xref:System.Windows.UIElement>.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia podstawową strukturę służącą do definiowania elementów wizualizacji. W poniższej tabeli wymieniono typy podstawowe używane podczas tworzenia obiektów i ich przeznaczenia. Poniżej przedstawiono kilka przykładów użycia:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Abstrakcyjna klasa bazowa, z której są dziedziczone wszystkie konkretne implementacje modułu definiowania układu.|
|<xref:System.Windows.Documents.AdornerLayer>|Klasa reprezentująca warstwę renderowania dla modułów definiowania układu dla co najmniej jednego elementu z.|
|<xref:System.Windows.Documents.AdornerDecorator>|Klasa, która umożliwia skojarzenie warstwy modułu definiowania układu z kolekcją elementów.|

## <a name="implementing-a-custom-adorner"></a>Implementowanie niestandardowego modułu definiowania układu

Struktura modułów definiowania układu dostarczana przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest przeznaczona głównie do obsługi tworzenia niestandardowych modułów definiowania. Niestandardowy moduł definiowania układu jest tworzony przez implementację klasy, która dziedziczy z klasy abstrakcyjnej <xref:System.Windows.Documents.Adorner>.

> [!NOTE]
> Elementem nadrzędnym <xref:System.Windows.Documents.Adorner> jest <xref:System.Windows.Documents.AdornerLayer>, który renderuje <xref:System.Windows.Documents.Adorner>, a nie element, który jest podpisywany.

Poniższy przykład przedstawia klasę implementującą prosty moduł definiowania układu. Przykładowy moduł definiowania układu po prostu tworzy rogi <xref:System.Windows.UIElement> za pomocą okręgów.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
Na poniższej ilustracji przedstawiono SimpleCircleAdorner zastosowany do <xref:System.Windows.Controls.TextBox>:

![Zrzut ekranu pokazujący pole tekstowe z tekstem.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Zachowanie renderowania dla modułów definiowania układu

Należy zauważyć, że moduły definiowania układu nie uwzględniają nieodłącznego zachowania renderowania; upewnienie się, że moduł definiowania układu jest odpowiedzialny za implementację modułu definiowania układu. Typowym sposobem implementacji zachowania renderowania jest zastąpienie metody <xref:System.Windows.UIElement.OnRender%2A> i użycie co najmniej jednego obiektu <xref:System.Windows.Media.DrawingContext> do renderowania wizualizacji modułu definiowania układu w miarę potrzeb (jak pokazano w powyższym przykładzie).

> [!NOTE]
> Wszystkie elementy umieszczone w warstwie modułu definiowania układu są renderowane na podstawie pozostałych ustawionych stylów. Innymi słowy, moduły definiowania układu zawsze są widoczne na górze i nie mogą zostać zastąpione przy użyciu kolejności z.

## <a name="events-and-hit-testing"></a>Testy zdarzeń i trafień

Moduły definiowania układu odbierają zdarzenia wejściowe podobnie jak wszystkie inne <xref:System.Windows.FrameworkElement>.  Ze względu na to, że moduł definiowania układu zawsze ma wyższy porządek osi z, od elementu, który jest jego podstawą, moduł definiowania układu odbiera zdarzenia wejściowe (takie jak <xref:System.Windows.UIElement.Drop> lub <xref:System.Windows.UIElement.MouseMove>), które mogą być przeznaczone dla bazowego elementu.  Moduł definiowania układu może nasłuchiwać określonych zdarzeń wejściowych i przekazać je do podstawowego elementu z własnym elementem, przez ponowne podnoszenie poziomu zdarzenia.

Aby włączyć przekazywanie testów trafień elementów pod modułem definiowania układu, ustaw właściwość <xref:System.Windows.UIElement.IsHitTestVisible%2A> testu trafień na **wartość false** dla modułu definiowania układu.  Aby uzyskać więcej informacji na temat testowania trafień, zobacz [test trafień w warstwie wizualnej](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Określanie układu pojedynczego elementu UIElement

Aby powiązać moduł definiowania układu z konkretną <xref:System.Windows.UIElement>, wykonaj następujące kroki:

1. Wywołaj metodę statyczną <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>, aby uzyskać obiekt <xref:System.Windows.Documents.AdornerLayer> dla <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> przeprowadzi drzewo wizualizacji, zaczynając od określonego <xref:System.Windows.UIElement>, i zwróci początkową warstwę modułu definiowania układu. (Jeśli nie zostaną znalezione żadne warstwy modułu definiowania układu, metoda zwróci wartość null).

2. Wywołaj metodę <xref:System.Windows.Documents.AdornerLayer.Add%2A>, aby powiązać moduł definiowania układu z <xref:System.Windows.UIElement>ą docelową.

 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej) z <xref:System.Windows.Controls.TextBox> *o nazwie:*

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> Używanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do powiązania modułu definiowania układu z innym elementem nie jest obecnie obsługiwane.

## <a name="adorning-the-children-of-a-panel"></a>Określanie układu elementów podrzędnych panelu

Aby powiązać moduł definiowania układu z elementami podrzędnymi <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:

1. Wywołaj metodę `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>, aby znaleźć warstwę modułu definiowania układu dla elementu, którego elementy podrzędne mają być podłączane.

2. Wylicz elementy podrzędne elementu nadrzędnego i Wywołaj metodę <xref:System.Windows.Documents.AdornerLayer.Add%2A>, aby powiązać moduł definiowania układu z każdym elementem podrzędnym.

Poniższy przykład wiąże SimpleCircleAdorner (pokazany powyżej) z elementami podrzędnymi <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*:

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Rysowanie obiektów — przegląd](../graphics-multimedia/drawing-objects-overview.md)
- [Tematy z instrukcjami](adorners-how-to-topics.md)
