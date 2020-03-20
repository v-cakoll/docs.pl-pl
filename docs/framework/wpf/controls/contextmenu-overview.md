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
# <a name="contextmenu-overview"></a><span data-ttu-id="54741-102">ContextMenu — Przegląd</span><span class="sxs-lookup"><span data-stu-id="54741-102">ContextMenu Overview</span></span>
<span data-ttu-id="54741-103">Klasa <xref:System.Windows.Controls.ContextMenu> reprezentuje element, który udostępnia funkcje przy <xref:System.Windows.Controls.Menu>użyciu kontekstu specyficznego dla kontekstu .</span><span class="sxs-lookup"><span data-stu-id="54741-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="54741-104">Zazwyczaj użytkownik udostępnia <xref:System.Windows.Controls.ContextMenu> w tym, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] klikając prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="54741-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="54741-105">W tym temacie <xref:System.Windows.Controls.ContextMenu> przedstawiono element i zawiera przykłady, jak go używać w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kodu.</span><span class="sxs-lookup"><span data-stu-id="54741-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a><span data-ttu-id="54741-106">Kontrola kontekstu</span><span class="sxs-lookup"><span data-stu-id="54741-106">ContextMenu Control</span></span>  
 <span data-ttu-id="54741-107">A <xref:System.Windows.Controls.ContextMenu> jest dołączony do określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="54741-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="54741-108">Element <xref:System.Windows.Controls.ContextMenu> umożliwia przedstawienie użytkownikom listy elementów, które określają polecenia lub opcje, które są skojarzone <xref:System.Windows.Controls.Button>z określonym formancie, na przykład .</span><span class="sxs-lookup"><span data-stu-id="54741-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="54741-109">Użytkownicy kliknij prawym przyciskiem myszy formant, aby menu było wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="54741-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="54741-110">Zazwyczaj kliknięcie podmenu <xref:System.Windows.Controls.MenuItem> powoduje, że aplikacja wykonuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="54741-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a><span data-ttu-id="54741-111">Tworzenie narzędzia ContextMenus</span><span class="sxs-lookup"><span data-stu-id="54741-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="54741-112">Poniższe przykłady pokazują, <xref:System.Windows.Controls.ContextMenu> jak utworzyć z podmenu.</span><span class="sxs-lookup"><span data-stu-id="54741-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="54741-113">Formanty <xref:System.Windows.Controls.ContextMenu> są dołączone do formantów przycisków.</span><span class="sxs-lookup"><span data-stu-id="54741-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="54741-114">Stosowanie stylów do menu kontekstowego</span><span class="sxs-lookup"><span data-stu-id="54741-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="54741-115">Za pomocą <xref:System.Windows.Style>formantu , można radykalnie zmienić wygląd i zachowanie <xref:System.Windows.Controls.ContextMenu> bez pisania formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="54741-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="54741-116">Oprócz ustawiania właściwości wizualnych, można również zastosować style do części formantu.</span><span class="sxs-lookup"><span data-stu-id="54741-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="54741-117">Na przykład można zmienić zachowanie części formantu za pomocą właściwości lub dodać części do lub <xref:System.Windows.Controls.ContextMenu>zmienić układ .</span><span class="sxs-lookup"><span data-stu-id="54741-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="54741-118">W poniższych przykładach przedstawiono <xref:System.Windows.Controls.ContextMenu> kilka sposobów dodawania stylów do formantów.</span><span class="sxs-lookup"><span data-stu-id="54741-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="54741-119">Pierwszy przykład definiuje styl `SimpleSysResources`o nazwie , który pokazuje, jak używać bieżących ustawień systemowych w stylu.</span><span class="sxs-lookup"><span data-stu-id="54741-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="54741-120">Przykład przypisuje <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> kolor <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> i <xref:System.Windows.Controls.Control.Foreground%2A> kolor <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="54741-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="54741-121">W poniższym przykładzie <xref:System.Windows.Trigger> użyto elementu <xref:System.Windows.Controls.Menu> do zmiany wyglądu w <xref:System.Windows.Controls.ContextMenu>odpowiedzi na zdarzenia, które są wywoływane w .</span><span class="sxs-lookup"><span data-stu-id="54741-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="54741-122">Gdy użytkownik przesuwa wskaźnik myszy nad menu, <xref:System.Windows.Controls.ContextMenu> wygląd elementów zmienia się.</span><span class="sxs-lookup"><span data-stu-id="54741-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54741-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54741-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="54741-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="54741-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="54741-125">ContextMenu — style i szablony</span><span class="sxs-lookup"><span data-stu-id="54741-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="54741-126">Przykład galerii kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="54741-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
