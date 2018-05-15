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
---
# <a name="contextmenu-overview"></a><span data-ttu-id="39dac-102">ContextMenu — Przegląd</span><span class="sxs-lookup"><span data-stu-id="39dac-102">ContextMenu Overview</span></span>
<span data-ttu-id="39dac-103"><xref:System.Windows.Controls.ContextMenu> Klasa reprezentuje element, który udostępnia funkcje przy użyciu określonego kontekstu <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="39dac-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="39dac-104">Zazwyczaj użytkownik udostępnia <xref:System.Windows.Controls.ContextMenu> w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przez kliknięcie prawym przyciskiem myszy przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="39dac-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="39dac-105">W tym temacie przedstawiono <xref:System.Windows.Controls.ContextMenu> elementu oraz przykłady sposobu używania go w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod.</span><span class="sxs-lookup"><span data-stu-id="39dac-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="39dac-106">ContextMenu — formant</span><span class="sxs-lookup"><span data-stu-id="39dac-106">ContextMenu Control</span></span>  
 <span data-ttu-id="39dac-107">A <xref:System.Windows.Controls.ContextMenu> jest dołączona do określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="39dac-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="39dac-108"><xref:System.Windows.Controls.ContextMenu> Element umożliwia przedstawia użytkowników z listą elementów, które określają poleceń i opcji, które są skojarzone z określonego formantu, na przykład <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="39dac-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="39dac-109">Użytkownicy kliknij prawym przyciskiem myszy formantu dokonanie menu są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="39dac-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="39dac-110">Zwykle, klikając pozycję <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja do wykonania polecenia.</span><span class="sxs-lookup"><span data-stu-id="39dac-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="39dac-111">Tworzenie ContextMenus</span><span class="sxs-lookup"><span data-stu-id="39dac-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="39dac-112">W poniższych przykładach pokazano, jak utworzyć <xref:System.Windows.Controls.ContextMenu> z podmenu.</span><span class="sxs-lookup"><span data-stu-id="39dac-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="39dac-113"><xref:System.Windows.Controls.ContextMenu> Formanty są dołączone do kontrolek przycisku.</span><span class="sxs-lookup"><span data-stu-id="39dac-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="39dac-114">Stosowanie stylów do ContextMenu</span><span class="sxs-lookup"><span data-stu-id="39dac-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="39dac-115">Za pomocą formantu <xref:System.Windows.Style>, można znacznie zmienić wygląd i zachowanie <xref:System.Windows.Controls.ContextMenu> bez pisania kontrolkę niestandardową.</span><span class="sxs-lookup"><span data-stu-id="39dac-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="39dac-116">Poza ustawieniem właściwości wizualnego, można również stosować style do części kontrolki.</span><span class="sxs-lookup"><span data-stu-id="39dac-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="39dac-117">Na przykład można zmienić zachowanie części formantu przy użyciu właściwości lub części, aby dodać lub zmienić układ, <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="39dac-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="39dac-118">W poniższych przykładach pokazano kilka sposobów dodawania stylów <xref:System.Windows.Controls.ContextMenu> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="39dac-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="39dac-119">Pierwszym przykładzie definiuje styl o nazwie `SimpleSysResources`, która przedstawia sposób użycia bieżące ustawienia systemu swojego stylu.</span><span class="sxs-lookup"><span data-stu-id="39dac-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="39dac-120">Przypisywane <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> kolorów i <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> kolor <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="39dac-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="39dac-121">W poniższym przykładzie użyto <xref:System.Windows.Trigger> elementu, aby zmienić wygląd <xref:System.Windows.Controls.Menu> w odpowiedzi na zdarzenia, które są generowane na <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="39dac-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="39dac-122">Gdy użytkownik przesuwa wskaźnik myszy nad menu wygląd <xref:System.Windows.Controls.ContextMenu> elementy zmiany.</span><span class="sxs-lookup"><span data-stu-id="39dac-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39dac-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39dac-123">See Also</span></span>  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [<span data-ttu-id="39dac-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="39dac-124">ContextMenu</span></span>](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [<span data-ttu-id="39dac-125">ContextMenu — style i szablony</span><span class="sxs-lookup"><span data-stu-id="39dac-125">ContextMenu Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [<span data-ttu-id="39dac-126">Przykładu z galerii formantów WPF</span><span class="sxs-lookup"><span data-stu-id="39dac-126">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
