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
ms.openlocfilehash: b70387e604b0917d154fc056b904e9ee05f6fbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557241"
---
# <a name="tooltip-overview"></a>ToolTip — Przegląd
Etykietka narzędzia jest mała okno podręczne pojawia się po zatrzymaniu wskaźnika myszy nad elementem, takie jak ponad <xref:System.Windows.Controls.Button>. W tym temacie przedstawiono wskazówki i opisano, jak tworzyć i dostosowywać zawartość etykietka narzędzia.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Co to jest etykietka narzędzia?  
 Gdy użytkownik przesuwa wskaźnik myszy nad elementem ma etykietka narzędzia, zostanie wyświetlone okno z zawartością etykietki narzędzia (na przykład tekstu zawierającego opis funkcji formantu), która określoną ilość czasu. Jeśli użytkownik przesuwa wskaźnik myszy formantu, okno zniknie, ponieważ zawartość etykietki narzędzia nie można ustawić fokusu.  
  
 Zawartość etykietka narzędzia może zawierać jeden lub więcej wierszy tekstu, obrazów, kształtów lub innych zawartości wizualnej. Należy zdefiniować etykietkę narzędzia dla kontrolki ustawiając jedną z następujących właściwości zawartości etykietka narzędzia.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Właściwości, których używasz zależy od tego, czy formant, który definiuje element tooltip dziedziczy <xref:System.Windows.FrameworkContentElement> lub <xref:System.Windows.FrameworkElement> klasy.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Etykietka narzędzia tworzenia  
 Poniższy przykład przedstawia sposób utworzyć prosty etykietka narzędzia, ustawiając <xref:System.Windows.FrameworkElement.ToolTip%2A> właściwości dla <xref:System.Windows.Controls.Button> kontroli ciąg tekstowy.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Można również zdefiniować jako etykietka narzędzia <xref:System.Windows.Controls.ToolTip> obiektu. W poniższym przykładzie użyto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do określenia <xref:System.Windows.Controls.ToolTip> obiektu jako etykietka narzędzia <xref:System.Windows.Controls.TextBox> elementu. Należy pamiętać, że w przykładzie określono <xref:System.Windows.Controls.ToolTip> przez ustawienie <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> właściwości.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 W poniższym przykładzie użyto kod można wygenerować <xref:System.Windows.Controls.ToolTip> obiektu. W przykładzie jest tworzony <xref:System.Windows.Controls.ToolTip> (`tt`) i kojarzy ją z <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Można również utworzyć zawartość etykietka narzędzia, która nie jest zdefiniowany jako <xref:System.Windows.Controls.ToolTip> obiektu otaczającej zawartości etykietki narzędzia w elemencie układu, takich jak <xref:System.Windows.Controls.DockPanel>. Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.FrameworkElement.ToolTip%2A> właściwość <xref:System.Windows.Controls.TextBox> do zawartości, która jest zawarta w <xref:System.Windows.Controls.DockPanel> formantu.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Przy użyciu właściwości etykietka narzędzia i ToolTipService klas  
 Etykietka narzędzia zawartości można dostosować przez ustawienie właściwości wizualnego i stosowanie stylów. W przypadku definiowania zawartości jako etykietka narzędzia <xref:System.Windows.Controls.ToolTip> obiektu, można ustawić właściwości visual <xref:System.Windows.Controls.ToolTip> obiektu. W przeciwnym razie należy ustawić na równoważne dołączone właściwości <xref:System.Windows.Controls.ToolTipService> klasy.  
  
 Na przykład ustawiania właściwości, aby określić położenie zawartości etykietka narzędzia, za pomocą <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> właściwości, zobacz [umieść etykietka narzędzia](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Style etykietki narzędzia  
 Styl możesz <xref:System.Windows.Controls.ToolTip> , definiując własne <xref:System.Windows.Style>. W poniższym przykładzie zdefiniowano <xref:System.Windows.Style> o nazwie `Simple` który pokazuje, jak przesunięcie rozmieszczenia <xref:System.Windows.Controls.ToolTip> i zmień jego wygląd przez ustawienie <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Za pomocą właściwości interwału czasu ToolTipService  
 <xref:System.Windows.Controls.ToolTipService> Klasa udostępnia następujące właściwości można ustawić tooltip wyświetlić razy: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Użyj <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> właściwości, aby określić opóźnienie, zwykle krótki, przed <xref:System.Windows.Controls.ToolTip> pojawia się, a także, aby określić, jak długo <xref:System.Windows.Controls.ToolTip> pozostaje widoczna. Aby uzyskać więcej informacji, zobacz [porady: opóźnienia wyświetlania etykietka narzędzia](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Właściwość określa etykietki narzędzi dla różnych formantów wyświetlane niezwłocznie początkowej podczas szybko przesuń wskaźnik myszy między nimi. Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> właściwości, zobacz [, użyj właściwości BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 Poniższy przykład przedstawia sposób ustawiania tych właściwości w etykietce narzędzia.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
