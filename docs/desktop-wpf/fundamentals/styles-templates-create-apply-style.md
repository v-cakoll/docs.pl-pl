---
title: Tworzenie stylu kontrolki
description: Dowiedz się, jak utworzyć i odwołać się do stylu kontrolki w Windows Presentation Foundation i .NET Core.
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
# <a name="create-a-style-for-a-control-in-wpf"></a>Tworzenie stylu kontrolki w WPF

Za pomocą Windows Presentation Foundation (WPF) można dostosować wygląd istniejącej kontrolki przy użyciu własnego stylu wielokrotnego użytku. Style można stosować globalnie do aplikacji, okien i stron lub bezpośrednio do kontrolek.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Tworzenie stylu

Można traktować <xref:System.Windows.Style> jako wygodny sposób zastosowania zestawu wartości właściwości do jednego lub większej liczby elementów. Możesz użyć stylu dla dowolnego elementu, który pochodzi <xref:System.Windows.FrameworkElement> od lub <xref:System.Windows.FrameworkContentElement> takich jak <xref:System.Windows.Window> lub. <xref:System.Windows.Controls.Button>

Najbardziej typowym sposobem deklarowania stylu jest jako zasób w `Resources` sekcji w pliku XAML. Ponieważ style są zasobami, przestrzegają one tych samych reguł określania zakresu, które mają zastosowanie do wszystkich zasobów. Umieść po prostu, gdzie deklarujesz styl, ma wpływ na miejsce, w którym można zastosować styl. Na przykład, Jeśli zadeklarujesz styl w głównym elemencie pliku XAML definicji aplikacji, styl może być używany w dowolnym miejscu w aplikacji.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Jeśli zadeklarujesz styl w jednej z plików XAML aplikacji, styl może być używany tylko w tym pliku XAML. Aby uzyskać więcej informacji na temat określania zakresu reguł dla zasobów, zobacz [zasoby XAML](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Styl składa się z `<Setter>` elementów podrzędnych, które ustawiają właściwości dla elementów, do których zastosowano styl. W powyższym przykładzie należy zauważyć, że styl jest ustawiony do zastosowania `TextBlock` do typów za `TargetType` pomocą atrybutu. <xref:System.Windows.Controls.Control.FontSize%2A> Styl ustawi ustawienia `15` na i <xref:System.Windows.Controls.Control.FontWeight%2A> do. `ExtraBold` Dodaj `<Setter>` dla każdej właściwości zmiany stylu.

## <a name="apply-a-style-implicitly"></a>Zastosuj styl niejawnie

A <xref:System.Windows.Style> jest wygodnym sposobem zastosowania zestawu wartości właściwości do więcej niż jednego elementu. Rozważmy na przykład następujące <xref:System.Windows.Controls.TextBlock> elementy i ich domyślny wygląd w oknie.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Przykładowy zrzut ekranu z stylem](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Wygląd domyślny można zmienić przez ustawienie właściwości, takich jak <xref:System.Windows.Controls.Control.FontSize%2A> i <xref:System.Windows.Controls.Control.FontFamily%2A>, dla każdego <xref:System.Windows.Controls.TextBlock> elementu bezpośrednio. Jeśli jednak chcesz, aby <xref:System.Windows.Controls.TextBlock> elementy mogły udostępniać pewne właściwości, możesz utworzyć <xref:System.Windows.Style> w `Resources` sekcji pliku XAML, jak pokazano poniżej.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Gdy ustawisz <xref:System.Windows.Style.TargetType%2A> styl na <xref:System.Windows.Controls.TextBlock> typ i pominięto `x:Key` atrybut, styl zostanie zastosowany do wszystkich elementów w <xref:System.Windows.Controls.TextBlock> zakresie stylu, który jest zazwyczaj plikiem XAML.

Teraz <xref:System.Windows.Controls.TextBlock> elementy pojawiają się w następujący sposób.

![Przykładowy zrzut ekranu z stylem](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Zastosuj styl jawnie

Jeśli dodasz `x:Key` atrybut o wartości do stylu, styl nie zostanie już niejawnie zastosowany do wszystkich elementów <xref:System.Windows.Style.TargetType%2A>. Tylko elementy, które jawnie odwołują się do stylu, będą miały styl zastosowany do nich.

Oto styl z poprzedniej sekcji, ale zadeklarowany przy użyciu `x:Key` atrybutu.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Aby zastosować styl, ustaw <xref:System.Windows.FrameworkElement.Style%2A> właściwość elementu na `x:Key` wartość przy użyciu [rozszerzenia znacznika StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md), jak pokazano poniżej.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

Należy zauważyć, że <xref:System.Windows.Controls.TextBlock> do pierwszego elementu jest stosowany styl, podczas gdy drugi element TextBlock pozostaje niezmieniony. Styl niejawny z poprzedniej sekcji został zmieniony na styl, który zadeklaruje `x:Key` atrybut, co oznacza, że jedynym elementem, którego dotyczy styl, jest ten, który odwołuje się bezpośrednio do stylu.

![Przykładowy zrzut ekranu z stylem](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "Create-a-style-Explicit-TextBlock")

Gdy styl jest stosowany, jawnie lub niejawnie, zostanie zapieczętowany i nie można go zmienić. Jeśli chcesz zmienić styl, który został zastosowany, Utwórz nowy styl, aby zastąpić istniejący. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style.IsSealed%2A> właściwość.

Można utworzyć obiekt, który wybiera styl do zastosowania na podstawie logiki niestandardowej. Aby zapoznać się z przykładem, zobacz przykład podanym dla <xref:System.Windows.Controls.StyleSelector> klasy.

## <a name="apply-a-style-programmatically"></a>Programistyczne stosowanie stylu

Aby programowo przypisać nazwany styl do elementu, Pobierz styl z kolekcji Resources i przypisz go do <xref:System.Windows.FrameworkElement.Style%2A> właściwości elementu. Elementy w kolekcji zasobów są typu <xref:System.Object>. W związku z tym należy rzutować pobrany styl na <xref:System.Windows.Style?displayProperty=fullName> przed przypisaniem go `Style` do właściwości. Na przykład poniższy kod ustawia styl `TextBlock` o nazwie `textblock1` do zdefiniowanego stylu. `TitleText`

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Poszerzenie stylu

Być może chcesz, aby <xref:System.Windows.Controls.TextBlock> dwa elementy współdzielli pewne wartości właściwości, takie <xref:System.Windows.Controls.Control.FontFamily%2A> jak i środkowo <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. Ale chcesz również, aby tekst **Moje obrazy** miał kilka dodatkowych właściwości. Można to zrobić, tworząc nowy styl oparty na pierwszym stylu, jak pokazano poniżej.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Ten `TextBlock` styl jest teraz wyśrodkowany, używa `Comic Sans MS` czcionki o rozmiarze `26`i koloru pierwszego planu do <xref:System.Windows.Media.LinearGradientBrush> pokazanego w przykładzie. Zwróć uwagę, że zastępuje <xref:System.Windows.Controls.Control.FontSize%2A> ona wartość stylu bazowego. Jeśli istnieje więcej niż jedna <xref:System.Windows.Setter> wskazująca na tę samą właściwość w, <xref:System.Windows.Style>obiekt, `Setter` który jest zadeklarowany jako ostatni ma pierwszeństwo.

Poniżej pokazano, <xref:System.Windows.Controls.TextBlock> jak wyglądają teraz elementy:

![Style — bloki tekstu](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Ten `TitleText` styl rozszerza styl, który został utworzony dla <xref:System.Windows.Controls.TextBlock> typu, do którego odwołuje `BasedOn="{StaticResource {x:Type TextBlock}}"`się. Możesz również zwiększyć styl, który ma `x:Key` za pomocą `x:Key` stylu. Na przykład, jeśli istnieje styl o nazwie `Header1` i chcesz go zwiększyć, użyj. `BasedOn="{StaticResource Header1}"`

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relacja właściwości TargetType i atrybutu x:Key

Jak pokazano <xref:System.Windows.Style.TargetType%2A> wcześniej, ustawienie właściwości na `TextBlock` bez przypisywania stylu `x:Key` powoduje, że styl ma być zastosowany do <xref:System.Windows.Controls.TextBlock> wszystkich elementów. W tym przypadku `x:Key` jest to niejawnie ustawione na `{x:Type TextBlock}`. Oznacza to, że jeśli jawnie ustawisz `x:Key` wartość na coś innego niż `{x:Type TextBlock}`, <xref:System.Windows.Style> nie jest ona automatycznie stosowana `TextBlock` do wszystkich elementów. Zamiast tego należy zastosować styl (przy użyciu `x:Key` wartości) do `TextBlock` elementów jawnie. Jeśli styl znajduje się w sekcji zasobów i nie ustawisz `TargetType` właściwości stylu, należy ustawić `x:Key` atrybut.

Oprócz podania wartości domyślnej dla `x:Key`, `TargetType` Właściwość określa typ, do którego mają zastosowanie właściwości setter. Jeśli nie określisz elementu `TargetType`, musisz zakwalifikować właściwości w <xref:System.Windows.Setter> obiektach za pomocą nazwy klasy przy użyciu składni. `Property="ClassName.Property"` Na `Property="FontSize"`przykład zamiast ustawienia, należy ustawić <xref:System.Windows.Setter.Property%2A> na `"TextBlock.FontSize"` lub. `"Control.FontSize"`

Należy również zauważyć, że wiele kontrolek WPF składa się z kombinacji innych formantów WPF. Jeśli utworzysz styl stosowany do wszystkich kontrolek typu, możesz uzyskać nieoczekiwane wyniki. Na przykład jeśli utworzysz styl, który jest <xref:System.Windows.Controls.TextBlock> przeznaczony dla typu w <xref:System.Windows.Window>, styl zostanie zastosowany do wszystkich `TextBlock` kontrolek w oknie, nawet jeśli `TextBlock` jest częścią innej kontrolki, takiej jak. <xref:System.Windows.Controls.ListBox>

## <a name="see-also"></a>Zobacz też

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [Przegląd zasobów XAML](xaml-resources-define.md)
- [Przegląd XAML (WPF & .NET Core)](xaml.md)
