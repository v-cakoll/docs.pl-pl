---
title: 'Porady: dodawanie rozszerzeń do formantu ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: 61a79b9bbe101d7bf694240bdffdecee5187adf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182320"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="0e979-102">Porady: dodawanie rozszerzeń do formantu ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="0e979-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="0e979-103">Użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> kontrolki można zwiększyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0e979-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="0e979-104">Dodaj znaczniki wyboru, aby określić, czy funkcja jest włączona czy wyłączona, na przykład czy linijka jest wyświetlana wzdłuż marginesu aplikacji edytora tekstu, lub aby wskazać, który plik na liście plików jest wyświetlany, na przykład w menu **Okno.**</span><span class="sxs-lookup"><span data-stu-id="0e979-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="0e979-105">Dodaj obrazy, które wizualnie reprezentują polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="0e979-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="0e979-106">Wyświetlanie klawiszy skrótów w celu zapewnienia klawiatury alternatywnej dla myszy do wykonywania poleceń.</span><span class="sxs-lookup"><span data-stu-id="0e979-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="0e979-107">Na przykład naciśnięcie klawiszy CTRL+C powoduje wykonanie polecenia **Kopiuj.**</span><span class="sxs-lookup"><span data-stu-id="0e979-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="0e979-108">Wyświetlanie klawiszy dostępu w celu zapewnienia klawiatury alternatywnej dla myszy do nawigacji po menu.</span><span class="sxs-lookup"><span data-stu-id="0e979-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="0e979-109">Na przykład naciśnięcie klawiszy ALT+F powoduje wybranie menu **Plik.**</span><span class="sxs-lookup"><span data-stu-id="0e979-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="0e979-110">Pokaż paski separatora, aby pogrupować powiązane polecenia i uczynić menu bardziej czytelnymi.</span><span class="sxs-lookup"><span data-stu-id="0e979-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="0e979-111">Aby wyświetlić znacznik wyboru na poleceniu menu</span><span class="sxs-lookup"><span data-stu-id="0e979-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="0e979-112">Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> jego `true`właściwość na .</span><span class="sxs-lookup"><span data-stu-id="0e979-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="0e979-113">Spowoduje to <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> również `true`ustawienie właściwości na .</span><span class="sxs-lookup"><span data-stu-id="0e979-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="0e979-114">Tej procedury należy używać tylko wtedy, gdy polecenie menu ma być domyślnie zaznaczone, niezależnie od tego, czy jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="0e979-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="0e979-115">Aby wyświetlić znacznik wyboru, który zmienia stan przy każdym kliknięciu</span><span class="sxs-lookup"><span data-stu-id="0e979-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="0e979-116">Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość polecenia menu `true`na .</span><span class="sxs-lookup"><span data-stu-id="0e979-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="0e979-117">Aby dodać obraz do polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0e979-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="0e979-118">Ustaw <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwość polecenia menu na nazwę obrazu.</span><span class="sxs-lookup"><span data-stu-id="0e979-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="0e979-119">Jeśli <xref:System.Windows.Forms.ToolStripItemDisplayStyle> właściwość tego polecenia menu <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>jest ustawiona na lub , obraz nie może być wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="0e979-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e979-120">Margines obrazu może również wyświetlać znacznik wyboru, jeśli tak zdecydujesz.</span><span class="sxs-lookup"><span data-stu-id="0e979-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="0e979-121">Można również ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość obrazu `true`na , a obraz pojawi się z kreskowanym obramowaniem wokół niego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0e979-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="0e979-122">Aby wyświetlić klawisz skrótu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0e979-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="0e979-123">Ustaw właściwość polecenia <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> menu na żądaną kombinację klawiatury, taką jak CTRL+O `true`dla polecenia **Otwórz** menu, i ustaw właściwość na <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> .</span><span class="sxs-lookup"><span data-stu-id="0e979-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="0e979-124">Aby wyświetlić niestandardowe klawisze skrótów dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0e979-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="0e979-125">Ustaw właściwość polecenia <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> menu na żądaną kombinację klawiatury, taką jak CTRL+SHIFT+O, <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> a `true`nie SHIFT+CTRL+O, i ustaw właściwość na .</span><span class="sxs-lookup"><span data-stu-id="0e979-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="0e979-126">Aby wyświetlić klawisz dostępu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0e979-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="0e979-127">Po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości dla polecenia menu wprowadź ampersand (&) przed literą, którą chcesz podkreślić jako klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="0e979-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="0e979-128">Na przykład wpisanie <xref:System.Windows.Forms.ToolStripItem.Text%2A> jako właściwości elementu menu spowoduje wyświetlenie `&Open` polecenia menu wyświetlanego jako pióro <u>O.</u></span><span class="sxs-lookup"><span data-stu-id="0e979-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="0e979-129">Aby przejść do tego polecenia menu, naciśnij <xref:System.Windows.Forms.MenuStrip>klawisz ALT, aby skupić się na programie , a następnie naciśnij klawisz dostępu nazwy menu.</span><span class="sxs-lookup"><span data-stu-id="0e979-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="0e979-130">Po otwarciu menu i pokazaniu elementów z klawiszami dostępu wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.</span><span class="sxs-lookup"><span data-stu-id="0e979-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e979-131">Unikaj definiowania zduplikowanych klawiszy dostępu, takich jak dwukrotne definiowanie klawiszy ALT+F w tym samym systemie menu.</span><span class="sxs-lookup"><span data-stu-id="0e979-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="0e979-132">Nie można zagwarantować kolejności wyboru zduplikowanych kluczy dostępu.</span><span class="sxs-lookup"><span data-stu-id="0e979-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="0e979-133">Aby wyświetlić pasek separatora między poleceniami menu</span><span class="sxs-lookup"><span data-stu-id="0e979-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="0e979-134">Po zdefiniowaniu <xref:System.Windows.Forms.MenuStrip> i elementy, które będą <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> zawierać, użyj lub metody, aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> formanty do żądanej <xref:System.Windows.Forms.MenuStrip> kolejności.</span><span class="sxs-lookup"><span data-stu-id="0e979-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,
    ' and the Save and Exit menu commands to the top-level File menu,
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,
    // and the Save and Exit menu commands to the top-level File menu,
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0e979-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e979-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="0e979-136">MenuStrip — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="0e979-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
