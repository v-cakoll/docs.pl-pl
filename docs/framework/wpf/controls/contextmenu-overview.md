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
# <a name="contextmenu-overview"></a><span data-ttu-id="0a01f-102">ContextMenu — Przegląd</span><span class="sxs-lookup"><span data-stu-id="0a01f-102">ContextMenu Overview</span></span>
<span data-ttu-id="0a01f-103">Klasa <xref:System.Windows.Controls.ContextMenu> reprezentuje element, który ujawnia funkcjonalność przy użyciu <xref:System.Windows.Controls.Menu>specyficznych dla kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0a01f-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="0a01f-104">Zazwyczaj użytkownik uwidacznia <xref:System.Windows.Controls.ContextMenu> w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przez kliknięcie prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="0a01f-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="0a01f-105">W tym temacie przedstawiono element <xref:System.Windows.Controls.ContextMenu> i przedstawiono przykłady korzystania z niego w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kodzie.</span><span class="sxs-lookup"><span data-stu-id="0a01f-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="0a01f-106">Formant rozprzybornika</span><span class="sxs-lookup"><span data-stu-id="0a01f-106">ContextMenu Control</span></span>  
 <span data-ttu-id="0a01f-107"><xref:System.Windows.Controls.ContextMenu> jest dołączona do konkretnej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0a01f-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="0a01f-108">Element <xref:System.Windows.Controls.ContextMenu> umożliwia prezentowanie użytkowników z listą elementów, które określają polecenia lub opcje, które są skojarzone z konkretną kontrolką, na przykład <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="0a01f-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="0a01f-109">Kliknij prawym przyciskiem myszy kontrolkę, aby wyświetlić menu.</span><span class="sxs-lookup"><span data-stu-id="0a01f-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="0a01f-110">Zazwyczaj kliknięcie <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="0a01f-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="0a01f-111">Tworzenie autopostaci</span><span class="sxs-lookup"><span data-stu-id="0a01f-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="0a01f-112">W poniższych przykładach pokazano, jak utworzyć <xref:System.Windows.Controls.ContextMenu> z podmenumi.</span><span class="sxs-lookup"><span data-stu-id="0a01f-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="0a01f-113">Kontrolki <xref:System.Windows.Controls.ContextMenu> są dołączone do kontrolek przycisku.</span><span class="sxs-lookup"><span data-stu-id="0a01f-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="0a01f-114">Stosowanie stylów do elementu dostosowanego</span><span class="sxs-lookup"><span data-stu-id="0a01f-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="0a01f-115">Za pomocą <xref:System.Windows.Style>kontrolki, można znacząco zmienić wygląd i zachowanie <xref:System.Windows.Controls.ContextMenu> bez konieczności pisania kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="0a01f-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="0a01f-116">Oprócz ustawiania właściwości wizualnych, można również zastosować style do części formantu.</span><span class="sxs-lookup"><span data-stu-id="0a01f-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="0a01f-117">Na przykład można zmienić zachowanie części formantu przy użyciu właściwości lub dodać części do, lub zmienić układ, <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0a01f-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="0a01f-118">W poniższych przykładach przedstawiono kilka sposobów dodawania stylów do kontrolek <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0a01f-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="0a01f-119">Pierwszy przykład definiuje styl o nazwie `SimpleSysResources`, który pokazuje, jak używać bieżących ustawień systemu w stylu.</span><span class="sxs-lookup"><span data-stu-id="0a01f-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="0a01f-120">Przykład przypisuje <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako kolor <xref:System.Windows.Controls.Control.Background%2A> i <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> kolor <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0a01f-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="0a01f-121">Poniższy przykład używa elementu <xref:System.Windows.Trigger>, aby zmienić wygląd <xref:System.Windows.Controls.Menu> w odpowiedzi na zdarzenia, które są wywoływane w <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0a01f-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="0a01f-122">Gdy użytkownik przesuwa wskaźnik myszy nad menu, wygląd elementów <xref:System.Windows.Controls.ContextMenu> zmienia się.</span><span class="sxs-lookup"><span data-stu-id="0a01f-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0a01f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a01f-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="0a01f-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0a01f-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="0a01f-125">ContextMenu — style i szablony</span><span class="sxs-lookup"><span data-stu-id="0a01f-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="0a01f-126">Przykład galerii formantów WPF</span><span class="sxs-lookup"><span data-stu-id="0a01f-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
