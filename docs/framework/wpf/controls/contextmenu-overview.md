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
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185917"
---
# <a name="contextmenu-overview"></a>ContextMenu — Przegląd
Klasa <xref:System.Windows.Controls.ContextMenu> reprezentuje element, który udostępnia funkcje przy <xref:System.Windows.Controls.Menu>użyciu kontekstu specyficznego dla kontekstu . Zazwyczaj użytkownik udostępnia <xref:System.Windows.Controls.ContextMenu> w tym, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] klikając prawym przyciskiem myszy. W tym temacie <xref:System.Windows.Controls.ContextMenu> przedstawiono element i zawiera przykłady, jak go używać w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kodu.  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>Kontrola kontekstu  
 A <xref:System.Windows.Controls.ContextMenu> jest dołączony do określonego formantu. Element <xref:System.Windows.Controls.ContextMenu> umożliwia przedstawienie użytkownikom listy elementów, które określają polecenia lub opcje, które są skojarzone <xref:System.Windows.Controls.Button>z określonym formancie, na przykład . Użytkownicy kliknij prawym przyciskiem myszy formant, aby menu było wyświetlane. Zazwyczaj kliknięcie podmenu <xref:System.Windows.Controls.MenuItem> powoduje, że aplikacja wykonuje polecenie.  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>Tworzenie narzędzia ContextMenus  
 Poniższe przykłady pokazują, <xref:System.Windows.Controls.ContextMenu> jak utworzyć z podmenu. Formanty <xref:System.Windows.Controls.ContextMenu> są dołączone do formantów przycisków.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>Stosowanie stylów do menu kontekstowego  
 Za pomocą <xref:System.Windows.Style>formantu , można radykalnie zmienić wygląd i zachowanie <xref:System.Windows.Controls.ContextMenu> bez pisania formantu niestandardowego. Oprócz ustawiania właściwości wizualnych, można również zastosować style do części formantu. Na przykład można zmienić zachowanie części formantu za pomocą właściwości lub dodać części do lub <xref:System.Windows.Controls.ContextMenu>zmienić układ . W poniższych przykładach przedstawiono <xref:System.Windows.Controls.ContextMenu> kilka sposobów dodawania stylów do formantów.  
  
 Pierwszy przykład definiuje styl `SimpleSysResources`o nazwie , który pokazuje, jak używać bieżących ustawień systemowych w stylu. Przykład przypisuje <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> i <xref:System.Windows.Controls.Control.Foreground%2A> kolor <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 W poniższym przykładzie <xref:System.Windows.Trigger> użyto elementu <xref:System.Windows.Controls.Menu> do zmiany wyglądu w <xref:System.Windows.Controls.ContextMenu>odpowiedzi na zdarzenia, które są wywoływane w . Gdy użytkownik przesuwa wskaźnik myszy nad menu, <xref:System.Windows.Controls.ContextMenu> wygląd elementów zmienia się.  
  
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
- [Przykład galerii kontrolek WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
