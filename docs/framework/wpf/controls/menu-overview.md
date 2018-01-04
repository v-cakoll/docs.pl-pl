---
title: "Przegląd Menu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ab5092b1bc9db22390a18b2c1cb1ad5725a2037
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="menu-overview"></a><span data-ttu-id="a2d37-102">Przegląd Menu</span><span class="sxs-lookup"><span data-stu-id="a2d37-102">Menu Overview</span></span>
<span data-ttu-id="a2d37-103"><xref:System.Windows.Controls.Menu> Klasa umożliwia organizowanie elementów, skojarzonego z poleceniami i obsługi zdarzeń w porządku hierarchicznym.</span><span class="sxs-lookup"><span data-stu-id="a2d37-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="a2d37-104">Każdy <xref:System.Windows.Controls.Menu> element zawiera kolekcję <xref:System.Windows.Controls.MenuItem> elementów.</span><span class="sxs-lookup"><span data-stu-id="a2d37-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="a2d37-105">Formant menu</span><span class="sxs-lookup"><span data-stu-id="a2d37-105">Menu Control</span></span>  
 <span data-ttu-id="a2d37-106"><xref:System.Windows.Controls.Menu> Kontroli Wyświetla listę elementów, które Określ opcje dla aplikacji lub polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2d37-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="a2d37-107">Zwykle, klikając pozycję <xref:System.Windows.Controls.MenuItem> otwiera podmenu lub powoduje, że aplikacja do wykonania polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2d37-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="a2d37-108">Tworzenie menu</span><span class="sxs-lookup"><span data-stu-id="a2d37-108">Creating Menus</span></span>  
 <span data-ttu-id="a2d37-109">Poniższy przykład tworzy <xref:System.Windows.Controls.Menu> do manipulowania tekstu w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a2d37-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="a2d37-110"><xref:System.Windows.Controls.Menu> Zawiera <xref:System.Windows.Controls.MenuItem> obiekty używające <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, i <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości i <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, i <xref:System.Windows.Controls.MenuItem.Click> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a2d37-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="a2d37-111">Elementy MenuItem za pomocą skrótów klawiaturowych</span><span class="sxs-lookup"><span data-stu-id="a2d37-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="a2d37-112">Skróty klawiaturowe są kombinacji znaków, które mogą być wprowadzane z klawiatury do wywołania <xref:System.Windows.Controls.Menu> poleceń.</span><span class="sxs-lookup"><span data-stu-id="a2d37-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="a2d37-113">Na przykład skrót **kopiowania** jest klawisze CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="a2d37-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="a2d37-114">Istnieją dwie właściwości do użycia z skróty klawiaturowe i elementy menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> lub <xref:System.Windows.Controls.MenuItem.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2d37-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="a2d37-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="a2d37-115">InputGestureText</span></span>  
 <span data-ttu-id="a2d37-116">Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> właściwość do przypisania tekst skrótów klawiaturowych do <xref:System.Windows.Controls.MenuItem> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a2d37-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="a2d37-117">Skrót klawiaturowy zostanie tylko umieszczone w elemencie menu.</span><span class="sxs-lookup"><span data-stu-id="a2d37-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="a2d37-118">Kojarzy polecenie z <xref:System.Windows.Controls.MenuItem>.</span><span class="sxs-lookup"><span data-stu-id="a2d37-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="a2d37-119">Aplikacja musi obsługiwać danych wejściowych użytkownika do wykonania akcji.</span><span class="sxs-lookup"><span data-stu-id="a2d37-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="a2d37-120">Polecenie</span><span class="sxs-lookup"><span data-stu-id="a2d37-120">Command</span></span>  
 <span data-ttu-id="a2d37-121">Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.MenuItem.Command%2A> właściwość do skojarzenia **Otwórz** i **zapisać** poleceń z <xref:System.Windows.Controls.MenuItem> formantów.</span><span class="sxs-lookup"><span data-stu-id="a2d37-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="a2d37-122">Nie tylko właściwość polecenia skojarzyć polecenie ze <xref:System.Windows.Controls.MenuItem>, ale zawiera także tekst wejściowy gestu do użycia jako skrót.</span><span class="sxs-lookup"><span data-stu-id="a2d37-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="a2d37-123"><xref:System.Windows.Controls.MenuItem> Klasa ma również <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> właściwość, która określa, gdzie występuje polecenie elementu.</span><span class="sxs-lookup"><span data-stu-id="a2d37-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="a2d37-124">Jeśli <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nie jest ustawiona, element, który ma fokus klawiatury odbierze polecenie.</span><span class="sxs-lookup"><span data-stu-id="a2d37-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="a2d37-125">Aby uzyskać więcej informacji na temat poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2d37-125">For more information about commands, see [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="a2d37-126">Style menu</span><span class="sxs-lookup"><span data-stu-id="a2d37-126">Menu Styling</span></span>  
 <span data-ttu-id="a2d37-127">Z stylów formantu, można znacznie zmienić wygląd i zachowanie <xref:System.Windows.Controls.Menu> formanty bez konieczności pisania kontrolkę niestandardową.</span><span class="sxs-lookup"><span data-stu-id="a2d37-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="a2d37-128">Poza ustawieniem właściwości wizualnego, można także zastosować <xref:System.Windows.Style> do poszczególnych części kontrolki, zmianę zachowania części sterowanie za pośrednictwem właściwości, lub Dodaj dodatkowe części lub zmienianie układu formantu.</span><span class="sxs-lookup"><span data-stu-id="a2d37-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="a2d37-129">W poniższych przykładach pokazano kilka sposobów, aby dodać <xref:System.Windows.Style> do <xref:System.Windows.Controls.Menu> formantu.</span><span class="sxs-lookup"><span data-stu-id="a2d37-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="a2d37-130">W pierwszym przykładzie kodu definiuje <xref:System.Windows.Style> o nazwie `Simple` który przedstawia sposób użycia bieżące ustawienia systemu swojego stylu.</span><span class="sxs-lookup"><span data-stu-id="a2d37-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="a2d37-131">Kod przypisuje kolor `MenuHighlightBrush` jako kolor tła menu i `MenuTextBrush` jako menu Kolor pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="a2d37-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="a2d37-132">Zwróć uwagę, użyj klawiszy zasobów można przypisać Pędzle.</span><span class="sxs-lookup"><span data-stu-id="a2d37-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="a2d37-133">Następujące przykładowe używa <xref:System.Windows.Trigger> elementy, które pozwalają zmienić wygląd <xref:System.Windows.Controls.MenuItem> w odpowiedzi na zdarzenia występujące w <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="a2d37-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="a2d37-134">Gdy wskaźnik myszy przesuwa się nad <xref:System.Windows.Controls.Menu>, kolor pierwszego planu i właściwości czcionki elementów menu, zmienić.</span><span class="sxs-lookup"><span data-stu-id="a2d37-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a2d37-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2d37-135">See Also</span></span>  
 [<span data-ttu-id="a2d37-136">Przykładu z galerii formantów WPF</span><span class="sxs-lookup"><span data-stu-id="a2d37-136">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
