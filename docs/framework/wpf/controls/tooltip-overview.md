---
title: ToolTip — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181949"
---
# <a name="tooltip-overview"></a>ToolTip — Przegląd
Etykietka narzędzia to małe okno podręczne, które pojawia się, gdy użytkownik wstrzymuje wskaźnik myszy nad elementem, na przykład nad elementem <xref:System.Windows.Controls.Button>. W tym temacie przedstawiono etykietkę narzędzia i omówiono sposób tworzenia i dostosowywania zawartości etykietki narzędzi.  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>Co to jest etykietka narzędzia?  
 Gdy użytkownik przesuwa wskaźnik myszy nad elementem, który ma etykietkę narzędzia, okno zawierające zawartość etykietki narzędzia (na przykład zawartość tekstową opisującą funkcję formantu) pojawia się przez określony czas. Jeśli użytkownik przesuwa wskaźnik myszy od formantu, okno zniknie, ponieważ zawartość etykietki narzędzia nie może uzyskać fokusu.  
  
 Zawartość etykietki narzędzia może zawierać jeden lub więcej wierszy tekstu, obrazów, kształtów lub innej zawartości wizualnej. Etykietkę narzędzia można zdefiniować, ustawiając jedną z następujących właściwości zawartości etykietki narzędzia.  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Używana właściwość zależy od tego, czy formant definiujący etykietkę narzędzia dziedziczy z <xref:System.Windows.FrameworkContentElement> klasy lub. <xref:System.Windows.FrameworkElement>  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>Tworzenie etykietki narzędzia  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Windows.FrameworkElement.ToolTip%2A> prostą <xref:System.Windows.Controls.Button> etykietkę narzędzia, ustawiając właściwość formantu na ciąg tekstowy.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Etykietkę narzędzia można również <xref:System.Windows.Controls.ToolTip> zdefiniować jako obiekt. W poniższym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.ToolTip> przykładzie użyto do określenia <xref:System.Windows.Controls.TextBox> obiektu jako etykietki narzędzia elementu. Należy zauważyć, że <xref:System.Windows.Controls.ToolTip> w przykładzie określa przez ustawienie <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Poniższy przykład używa kodu <xref:System.Windows.Controls.ToolTip> do wygenerowania obiektu. Przykład tworzy <xref:System.Windows.Controls.ToolTip> (`tt`) i kojarzy <xref:System.Windows.Controls.Button>go z .  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Można również utworzyć zawartość etykietki narzędzi, <xref:System.Windows.Controls.ToolTip> która nie jest zdefiniowana jako obiekt, otaczając <xref:System.Windows.Controls.DockPanel>zawartość etykietki narzędzia w elemencie układu, takim jak . W poniższym przykładzie <xref:System.Windows.FrameworkElement.ToolTip%2A> pokazano, <xref:System.Windows.Controls.TextBox> jak ustawić właściwość zawartości <xref:System.Windows.Controls.DockPanel> a do zawartości, która jest ujęta w formancie.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Korzystanie z właściwości etykietek narzędzi i etykietek narzędziSłużyń  
 Zawartość etykietki narzędzi można dostosować, ustawiając właściwości wizualne i stosując style. Jeśli zawartość etykietki narzędzia <xref:System.Windows.Controls.ToolTip> zostanie zdefiniowana jako obiekt, można <xref:System.Windows.Controls.ToolTip> ustawić właściwości wizualne obiektu. W przeciwnym razie należy ustawić równoważne <xref:System.Windows.Controls.ToolTipService> dołączone właściwości w klasie.  
  
 Na przykład, jak ustawić właściwości w celu określenia położenia <xref:System.Windows.Controls.ToolTip> zawartości <xref:System.Windows.Controls.ToolTipService> etykietki narzędzi przy użyciu i właściwości, zobacz [Położenie etykietki narzędzia](how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>Stylizowanie etykietki narzędzia  
 Można stylizować, <xref:System.Windows.Controls.ToolTip> definiując niestandardowy <xref:System.Windows.Style>plik . Poniższy przykład definiuje <xref:System.Windows.Style> `Simple` wywołanie, które pokazuje, <xref:System.Windows.Controls.ToolTip> jak zrównoważyć położenie <xref:System.Windows.Controls.Control.Background%2A>i <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontSize%2A>zmienić <xref:System.Windows.Controls.Control.FontWeight%2A>jego wygląd, ustawiając , , , i .  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Korzystanie z właściwości interwału czasu etykietki narzędziaUsługa  
 Klasa <xref:System.Windows.Controls.ToolTipService> zawiera następujące właściwości, aby ustawić czas wyświetlania etykietki narzędzia: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Użyj <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> właściwości, aby określić opóźnienie, zazwyczaj <xref:System.Windows.Controls.ToolTip> krótkie, przed pojawia <xref:System.Windows.Controls.ToolTip> się, a także określić, jak długo pozostaje widoczne. Aby uzyskać więcej informacji, zobacz [Jak: Opóźnić wyświetlenie etykietki narzędzia](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).  
  
 Właściwość <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> określa, czy etykietki narzędzi dla różnych formantów pojawiają się bez początkowego opóźnienia podczas szybkiego przesuwania wskaźnika myszy między nimi. Aby uzyskać więcej <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> informacji na temat właściwości, zobacz [Korzystanie z właściwości BetweenShowDelay](how-to-use-the-betweenshowdelay-property.md).  
  
 W poniższym przykładzie pokazano, jak ustawić te właściwości dla etykietki narzędzia.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Tematy in jakże](tooltip-how-to-topics.md)
