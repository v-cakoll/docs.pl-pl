---
title: ContextMenu — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: e862f02e736cb8507dde5036700d751f8af0a226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552873"
---
# <a name="contextmenu-overview"></a>ContextMenu — Przegląd
<xref:System.Windows.Controls.ContextMenu> Klasa reprezentuje element, który udostępnia funkcje przy użyciu określonego kontekstu <xref:System.Windows.Controls.Menu>. Zazwyczaj użytkownik udostępnia <xref:System.Windows.Controls.ContextMenu> w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przez kliknięcie prawym przyciskiem myszy przycisk myszy. W tym temacie przedstawiono <xref:System.Windows.Controls.ContextMenu> elementu oraz przykłady sposobu używania go w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu — formant  
 A <xref:System.Windows.Controls.ContextMenu> jest dołączona do określonego formantu. <xref:System.Windows.Controls.ContextMenu> Element umożliwia przedstawia użytkowników z listą elementów, które określają poleceń i opcji, które są skojarzone z określonego formantu, na przykład <xref:System.Windows.Controls.Button>. Użytkownicy kliknij prawym przyciskiem myszy formantu dokonanie menu są wyświetlane. Zwykle, klikając pozycję <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja do wykonania polecenia.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Tworzenie ContextMenus  
 W poniższych przykładach pokazano, jak utworzyć <xref:System.Windows.Controls.ContextMenu> z podmenu. <xref:System.Windows.Controls.ContextMenu> Formanty są dołączone do kontrolek przycisku.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Stosowanie stylów do ContextMenu  
 Za pomocą formantu <xref:System.Windows.Style>, można znacznie zmienić wygląd i zachowanie <xref:System.Windows.Controls.ContextMenu> bez pisania kontrolkę niestandardową. Poza ustawieniem właściwości wizualnego, można również stosować style do części kontrolki. Na przykład można zmienić zachowanie części formantu przy użyciu właściwości lub części, aby dodać lub zmienić układ, <xref:System.Windows.Controls.ContextMenu>. W poniższych przykładach pokazano kilka sposobów dodawania stylów <xref:System.Windows.Controls.ContextMenu> kontrolki.  
  
 Pierwszym przykładzie definiuje styl o nazwie `SimpleSysResources`, która przedstawia sposób użycia bieżące ustawienia systemu swojego stylu. Przypisywane <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> kolorów i <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> kolor <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 W poniższym przykładzie użyto <xref:System.Windows.Trigger> elementu, aby zmienić wygląd <xref:System.Windows.Controls.Menu> w odpowiedzi na zdarzenia, które są generowane na <xref:System.Windows.Controls.ContextMenu>. Gdy użytkownik przesuwa wskaźnik myszy nad menu wygląd <xref:System.Windows.Controls.ContextMenu> elementy zmiany.  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [ContextMenu — style i szablony](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [Przykładu z galerii formantów WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
