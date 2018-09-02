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
ms.openlocfilehash: a11dcfc9030944365adda3656a8895912b0ef0d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399222"
---
# <a name="tooltip-overview"></a>ToolTip — Przegląd
Etykietka narzędzia jest niewielkie okno podręczne, który pojawia się po zatrzymaniu wskaźnika myszy nad elementem, takie jak ponad <xref:System.Windows.Controls.Button>. W tym temacie przedstawiono etykietkę narzędzia i w tym artykule omówiono sposób tworzenia i dostosować zawartość etykietki narzędzia.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Etykietka narzędzia co to jest?  
 Gdy użytkownik przesuwa wskaźnik myszy nad elementem, który ma etykietka narzędzia, przez określony przedział czasu pojawi się okno które zawiera zawartość etykietki narzędzia (na przykład, zawartości tekstowej opisujący funkcji formantu). Gdy użytkownik przesuwa wskaźnik myszy poza formant, okno znika, ponieważ zawartość etykietki narzędzi nie może otrzymać ostrości.  
  
 Zawartość etykietka narzędzia może zawierać jeden lub więcej wierszy tekstu, obrazów, kształtów lub innych zawartości wizualnej. Należy zdefiniować etykietkę narzędzia dla kontrolki, ustawiając jedną z następujących właściwości do zawartości etykietki narzędzia.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Właściwości, których używasz zależy od tego, czy formant, który definiuje etykietki narzędzia, o których dziedziczy <xref:System.Windows.FrameworkContentElement> lub <xref:System.Windows.FrameworkElement> klasy.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Tworzenie etykietki narzędzia  
 Poniższy przykład pokazuje, jak utworzyć proste etykietki narzędzia, ustawiając <xref:System.Windows.FrameworkElement.ToolTip%2A> właściwość <xref:System.Windows.Controls.Button> kontrolki na ciąg tekstowy.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Można również zdefiniować jako etykietka narzędzia <xref:System.Windows.Controls.ToolTip> obiektu. W poniższym przykładzie użyto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do określenia <xref:System.Windows.Controls.ToolTip> obiektu jako etykietka narzędzia <xref:System.Windows.Controls.TextBox> elementu. Należy zauważyć, że w przykładzie określono <xref:System.Windows.Controls.ToolTip> , ustawiając <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 W poniższym przykładzie użyto kod można wygenerować <xref:System.Windows.Controls.ToolTip> obiektu. W przykładzie jest tworzony <xref:System.Windows.Controls.ToolTip> (`tt`) i kojarzy ją z <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Można również tworzyć zawartość etykietki narzędzia, która nie jest zdefiniowany jako <xref:System.Windows.Controls.ToolTip> obiektu, umieszczając zawartości etykietki narzędzia w elemencie układu, takich jak <xref:System.Windows.Controls.DockPanel>. Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.FrameworkElement.ToolTip%2A> właściwość <xref:System.Windows.Controls.TextBox> do zawartości, który jest ujęty w <xref:System.Windows.Controls.DockPanel> kontroli.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Za pomocą właściwości klasy ToolTipService i etykietki narzędzi  
 Etykietka narzędzia zawartość można dostosować przez ustawienie właściwości wizualnego i stosowanie stylów. Jeśli zdefiniujesz zawartość jako etykietka narzędzia <xref:System.Windows.Controls.ToolTip> obiektu, można ustawić właściwości visual <xref:System.Windows.Controls.ToolTip> obiektu. W przeciwnym razie należy ustawić na równoważne dołączone właściwości <xref:System.Windows.Controls.ToolTipService> klasy.  
  
 Na przykład sposób ustawiania właściwości, aby określić położenie tooltip zawartości przy użyciu <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> właściwości, zobacz [położenie ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Ustawianie stylów etykietki narzędzia  
 Styl możesz <xref:System.Windows.Controls.ToolTip> przez zdefiniowanie niestandardowego <xref:System.Windows.Style>. W poniższym przykładzie zdefiniowano <xref:System.Windows.Style> o nazwie `Simple` pokazujący sposób przesunięcie rozmieszczenia <xref:System.Windows.Controls.ToolTip> i zmieniać jego wygląd poprzez ustawienie <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Za pomocą właściwości interwału czasu ToolTipService  
 <xref:System.Windows.Controls.ToolTipService> Udostępnia następujące właściwości można ustawić etykietkę narzędzia Wyświetl czas: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Użyj <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> właściwości, aby określić opóźnienie, zazwyczaj krótki, przed <xref:System.Windows.Controls.ToolTip> pojawia się i również, aby określić, jak długo <xref:System.Windows.Controls.ToolTip> pozostaje widoczna. Aby uzyskać więcej informacji, zobacz [jak: opóźnienie wyświetlania etykietka narzędzia](https://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Właściwość określa etykietki narzędzi dla formantów różne wyświetlane bez opóźnień początkowej podczas szybko przesuń wskaźnik myszy między nimi. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> właściwości, zobacz [Użyj właściwości BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 Poniższy przykład pokazuje, jak ustawić te właściwości jako etykietkę narzędzia.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
