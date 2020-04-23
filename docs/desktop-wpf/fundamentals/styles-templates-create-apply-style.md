---
title: Tworzenie stylu formantu
description: Dowiedz się, jak utworzyć i odwołać się do stylu sterowania w programie Windows Presentation Foundation i .NET Core.
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071270"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>Tworzenie stylu formantu w WPF

Za pomocą programu Windows Presentation Foundation (WPF) można dostosować wygląd istniejącego formantu za pomocą własnego stylu wielokrotnegoużynia. Style można stosować globalnie do aplikacji, okien i stron lub bezpośrednio do formantów.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Tworzenie stylu

Można myśleć <xref:System.Windows.Style> jako wygodny sposób, aby zastosować zestaw wartości właściwości do jednego lub więcej elementów. Można użyć stylu na dowolnym elemencie, <xref:System.Windows.Window> który <xref:System.Windows.Controls.Button>wywodzi się z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> takiego jak lub .

Najczęstszym sposobem deklarowania stylu jest jako `Resources` zasób w sekcji w pliku XAML. Ponieważ style są zasobami, są one zgodne z tymi samymi regułami zakresu, które mają zastosowanie do wszystkich zasobów. Mówiąc prościej, gdzie deklarujesz styl wpływa na to, gdzie można zastosować styl. Na przykład jeśli deklarujesz styl w elemencie głównym pliku XAML definicji aplikacji, styl może być używany w dowolnym miejscu w aplikacji.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Jeśli deklarujesz styl w jednym z plików XAML aplikacji, styl może być używany tylko w tym pliku XAML. Aby uzyskać więcej informacji na temat reguł określania zakresu zasobów, zobacz [Zasoby XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Styl składa się `<Setter>` z elementów podrzędnych, które ustawiają właściwości elementów, do których jest stosowany styl. W powyższym przykładzie należy zauważyć, że `TextBlock` styl `TargetType` jest ustawiony na zastosowanie do typów za pomocą atrybutu. Styl ustawi <xref:System.Windows.Controls.Control.FontSize%2A> do `15` i <xref:System.Windows.Controls.Control.FontWeight%2A> `ExtraBold`do . Dodaj `<Setter>` dla każdej właściwości zmiany stylu.

## <a name="apply-a-style-implicitly"></a>Stosowanie stylu niejawnie

A <xref:System.Windows.Style> jest wygodnym sposobem zastosowania zestawu wartości właściwości do więcej niż jednego elementu. Rozważmy na przykład <xref:System.Windows.Controls.TextBlock> następujące elementy i ich domyślny wygląd w oknie.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Przykładowy zrzut ekranu przedstawiający styl](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Wygląd domyślny można zmienić, ustawiając <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.Control.FontFamily%2A>właściwości, <xref:System.Windows.Controls.TextBlock> takie jak i , bezpośrednio na każdym elemencie. Jeśli jednak <xref:System.Windows.Controls.TextBlock> elementy mają współużytkować niektóre właściwości, możesz utworzyć <xref:System.Windows.Style> w `Resources` sekcji pliku XAML, jak pokazano poniżej.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Po ustawieniu <xref:System.Windows.Style.TargetType%2A> stylu na <xref:System.Windows.Controls.TextBlock> typ i pominięciu atrybutu `x:Key` styl jest stosowany <xref:System.Windows.Controls.TextBlock> do wszystkich elementów o zakresie do stylu, który jest zazwyczaj samym plikiem XAML.

Teraz <xref:System.Windows.Controls.TextBlock> elementy pojawiają się w następujący sposób.

![Przykładowy zrzut ekranu przedstawiający styl](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Jawnie stosowanie stylu

Jeśli dodasz `x:Key` atrybut z wartością do stylu, styl nie jest już <xref:System.Windows.Style.TargetType%2A>niejawnie stosowany do wszystkich elementów programu . Tylko elementy, które jawnie odwołują się do stylu będzie mieć styl stosowane do nich.

Oto styl z poprzedniej sekcji, ale `x:Key` zadeklarowany z atrybutem.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Aby zastosować styl, <xref:System.Windows.FrameworkElement.Style%2A> ustaw właściwość na `x:Key` elemencie do wartości, używając [rozszerzenia znaczników StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), jak pokazano poniżej.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Należy zauważyć, <xref:System.Windows.Controls.TextBlock> że pierwszy element ma styl zastosowany do niego, podczas gdy drugi TextBlock element pozostaje niezmieniona. Styl niejawny z poprzedniej sekcji został zmieniony na `x:Key` styl, który zadeklarował atrybut, co oznacza, że jedynym elementem, którego dotyczy styl, jest ten, który bezpośrednio odwołuje się do stylu.

![Przykładowy zrzut ekranu przedstawiający styl](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "create-a-style-explicit-textblock")

Po zastosowaniu stylu, jawnie lub niejawnie, staje się zapieczętowany i nie można go zmienić. Jeśli chcesz zmienić zastosowany styl, utwórz nowy styl, który zastąpi istniejący. Aby uzyskać więcej <xref:System.Windows.Style.IsSealed%2A> informacji, zobacz właściwość.

Można utworzyć obiekt, który wybiera styl do zastosowania na podstawie logiki niestandardowej. Na przykład zobacz przykład podany <xref:System.Windows.Controls.StyleSelector> dla klasy.

## <a name="apply-a-style-programmatically"></a>Programowo stosowanie stylu

Aby przypisać nazwany styl do elementu programowo, pobierz styl z kolekcji zasobów <xref:System.Windows.FrameworkElement.Style%2A> i przypisz go do właściwości elementu. Elementy w kolekcji zasobów <xref:System.Object>są typu . W związku z tym należy rzutować <xref:System.Windows.Style?displayProperty=fullName> pobrany styl `Style` do przed przypisaniem go do właściwości. Na przykład poniższy kod ustawia `TextBlock` styl `textblock1` o nazwie `TitleText`do zdefiniowanego stylu .

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Rozszerzanie stylu

Być może chcesz, aby dwa <xref:System.Windows.Controls.TextBlock> elementy współużytkować niektóre wartości właściwości, takie jak <xref:System.Windows.Controls.Control.FontFamily%2A> i wyśrodkowane <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. Ale chcesz również tekst **Moje obrazy** mają pewne dodatkowe właściwości. Można to zrobić, tworząc nowy styl, który jest oparty na pierwszym stylu, jak pokazano tutaj.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Ten `TextBlock` styl jest teraz wyśrodkowany, `Comic Sans MS` używa `26`czcionki o rozmiarze , <xref:System.Windows.Media.LinearGradientBrush> a kolor pierwszego planu ustawiony na pokazany w przykładzie. Należy zauważyć, że <xref:System.Windows.Controls.Control.FontSize%2A> zastępuje wartość stylu podstawowego. Jeśli istnieje więcej niż <xref:System.Windows.Setter> jeden wskazując na tę <xref:System.Windows.Style>samą właściwość w , `Setter` który jest zadeklarowany jako ostatni ma pierwszeństwo.

Poniżej przedstawiono, <xref:System.Windows.Controls.TextBlock> jak teraz wyglądają elementy:

![Stylizowane blokady tekstu](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Ten `TitleText` styl rozszerza styl, który został <xref:System.Windows.Controls.TextBlock> utworzony dla `BasedOn="{StaticResource {x:Type TextBlock}}"`typu, odwołuje się do . Można również rozszerzyć styl, `x:Key` który ma `x:Key` przy użyciu stylu. Na przykład, jeśli był `Header1` styl o nazwie i chcesz rozszerzyć `BasedOn="{StaticResource Header1}"`ten styl, należy użyć .

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relacja właściwości TargetType i atrybutu x:Key

Jak wcześniej pokazano, <xref:System.Windows.Style.TargetType%2A> ustawienie `TextBlock` właściwości bez przypisywania `x:Key` stylu powoduje, że styl <xref:System.Windows.Controls.TextBlock> ma być stosowany do wszystkich elementów. W takim przypadku `x:Key` jest niejawnie ustawiona na `{x:Type TextBlock}`. Oznacza to, że jeśli `x:Key` jawnie ustawić `{x:Type TextBlock}`wartość <xref:System.Windows.Style> na coś innego niż `TextBlock` , nie jest stosowany do wszystkich elementów automatycznie. Zamiast tego należy zastosować styl (przy `x:Key` użyciu wartości) do `TextBlock` elementów jawnie. Jeśli styl znajduje się w sekcji zasobów i `TargetType` nie ustawisz właściwości w `x:Key` stylu, należy ustawić atrybut.

Oprócz podania wartości domyślnej `x:Key`dla `TargetType` , właściwość określa typ, do którego mają zastosowanie właściwości ustawiacza. Jeśli nie określisz `TargetType`przycisku , należy zakwalifikować <xref:System.Windows.Setter> właściwości w obiektach o nazwie `Property="ClassName.Property"`klasy przy użyciu składni . Na przykład `Property="FontSize"`zamiast ustawiania , <xref:System.Windows.Setter.Property%2A> należy `"TextBlock.FontSize"` `"Control.FontSize"`ustawić lub .

Należy również zauważyć, że wiele formantów WPF składa się z kombinacji innych formantów WPF. Jeśli utworzysz styl, który ma zastosowanie do wszystkich formantów typu, może uzyskać nieoczekiwane wyniki. Na przykład, jeśli utworzysz <xref:System.Windows.Controls.TextBlock> styl, <xref:System.Windows.Window>który jest przeznaczony dla `TextBlock` typu w , styl `TextBlock` jest stosowany do wszystkich formantów w oknie, nawet jeśli jest częścią innego formantu, takiego jak <xref:System.Windows.Controls.ListBox>.

## <a name="see-also"></a>Zobacz też

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Omówienie zasobów XAML](xaml-resources-define.md)
- [Omówienie XAML (WPF & .NET Core)](xaml.md)
