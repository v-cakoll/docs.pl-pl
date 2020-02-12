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
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124367"
---
# <a name="contextmenu-overview"></a>ContextMenu — Przegląd
Klasa <xref:System.Windows.Controls.ContextMenu> reprezentuje element, który ujawnia funkcjonalność przy użyciu <xref:System.Windows.Controls.Menu>specyficznych dla kontekstu. Zazwyczaj użytkownik uwidacznia <xref:System.Windows.Controls.ContextMenu> w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przez kliknięcie prawym przyciskiem myszy. W tym temacie przedstawiono element <xref:System.Windows.Controls.ContextMenu> i przedstawiono przykłady korzystania z niego w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kodzie.  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Formant rozprzybornika  
 <xref:System.Windows.Controls.ContextMenu> jest dołączona do konkretnej kontrolki. Element <xref:System.Windows.Controls.ContextMenu> umożliwia prezentowanie użytkowników z listą elementów, które określają polecenia lub opcje, które są skojarzone z konkretną kontrolką, na przykład <xref:System.Windows.Controls.Button>. Kliknij prawym przyciskiem myszy kontrolkę, aby wyświetlić menu. Zazwyczaj kliknięcie <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja wykonuje polecenie.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Tworzenie autopostaci  
 W poniższych przykładach pokazano, jak utworzyć <xref:System.Windows.Controls.ContextMenu> z podmenumi. Kontrolki <xref:System.Windows.Controls.ContextMenu> są dołączone do kontrolek przycisku.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Stosowanie stylów do elementu dostosowanego  
 Za pomocą <xref:System.Windows.Style>kontrolki, można znacząco zmienić wygląd i zachowanie <xref:System.Windows.Controls.ContextMenu> bez konieczności pisania kontrolki niestandardowej. Oprócz ustawiania właściwości wizualnych, można również zastosować style do części formantu. Na przykład można zmienić zachowanie części formantu przy użyciu właściwości lub dodać części do, lub zmienić układ, <xref:System.Windows.Controls.ContextMenu>. W poniższych przykładach przedstawiono kilka sposobów dodawania stylów do kontrolek <xref:System.Windows.Controls.ContextMenu>.  
  
 Pierwszy przykład definiuje styl o nazwie `SimpleSysResources`, który pokazuje, jak używać bieżących ustawień systemu w stylu. Przykład przypisuje <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako kolor <xref:System.Windows.Controls.Control.Background%2A> i <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> kolor <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Poniższy przykład używa elementu <xref:System.Windows.Trigger>, aby zmienić wygląd <xref:System.Windows.Controls.Menu> w odpowiedzi na zdarzenia, które są wywoływane w <xref:System.Windows.Controls.ContextMenu>. Gdy użytkownik przesuwa wskaźnik myszy nad menu, wygląd elementów <xref:System.Windows.Controls.ContextMenu> zmienia się.  
  
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

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [ContextMenu](contextmenu.md)
- [ContextMenu — style i szablony](contextmenu-styles-and-templates.md)
- [Przykład galerii formantów WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
