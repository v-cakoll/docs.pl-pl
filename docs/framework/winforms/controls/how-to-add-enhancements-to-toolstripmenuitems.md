---
title: 'Instrukcje: dodawanie rozszerzeń do kontrolki ToolStripMenuItems'
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
ms.openlocfilehash: 458347df7e17aabc1e9e21d66ad1b5a96200fe28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198559"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="0b062-102">Instrukcje: dodawanie rozszerzeń do kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="0b062-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="0b062-103">Możesz zwiększyć użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> kontrolek w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0b062-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="0b062-104">Dodawanie znaczników zaznaczenia Określa, czy funkcja jest włączony lub wyłączony, takie jak czy linijki są wyświetlane wzdłuż marginesu edytora lub aby wskazać plik, który w postaci listy plików jest w trakcie wyświetlania, takich jak na **okna** menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="0b062-105">Dodawanie obrazów, które wizualnie przedstawiają poleceń menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="0b062-106">Wyświetlanie klawiszy skrótów, aby zapewnić klawiatury zamiast myszy do wykonywania poleceń.</span><span class="sxs-lookup"><span data-stu-id="0b062-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="0b062-107">Na przykład, naciskając klawisze CTRL + C, wykonuje **kopiowania** polecenia.</span><span class="sxs-lookup"><span data-stu-id="0b062-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="0b062-108">Wyświetlanie kluczy dostępu do zapewnienia klawiatury zamiast myszy menu nawigacji.</span><span class="sxs-lookup"><span data-stu-id="0b062-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="0b062-109">Na przykład, naciskając klawisze ALT + F wybiera **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="0b062-110">Wyświetlanie pasków separatorów grupować powiązane polecenia i zwiększyć czytelność menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="0b062-111">Aby wyświetlić znacznik wyboru na poleceniu menu</span><span class="sxs-lookup"><span data-stu-id="0b062-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="0b062-112">Ustaw jego <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0b062-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="0b062-113">Powoduje ono również ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0b062-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="0b062-114">Użyj tej procedury, tylko wtedy, gdy ma się wyświetlone jako zaznaczone domyślnie, niezależnie od tego, czy wybrano polecenie menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="0b062-115">Aby wyświetlić znacznik wyboru, który zmienia stan każdego kliknięciem</span><span class="sxs-lookup"><span data-stu-id="0b062-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="0b062-116">Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0b062-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="0b062-117">Aby dodać obraz do polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0b062-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="0b062-118">Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwość na nazwę obrazu.</span><span class="sxs-lookup"><span data-stu-id="0b062-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="0b062-119">Jeśli <xref:System.Windows.Forms.ToolStripItemDisplayStyle> tego polecenia menu jest właściwością <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nie można wyświetlić obrazu.</span><span class="sxs-lookup"><span data-stu-id="0b062-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b062-120">Margines obrazka można również pokazać znacznik wyboru Jeśli więc wybrano.</span><span class="sxs-lookup"><span data-stu-id="0b062-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="0b062-121">Ponadto można ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwości obrazu do `true`, a obraz pojawi się wraz z kreskowanym obramowaniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0b062-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="0b062-122">Aby wyświetlić klawisza skrótu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0b062-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="0b062-123">Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> właściwości z kombinacją żądaną klawiatury, takie jak CTRL + O, aby uzyskać **Otwórz** polecenia menu, a następnie ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0b062-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="0b062-124">Aby wyświetlić niestandardowe klawisze skrótu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0b062-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="0b062-125">Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwości z kombinacją żądaną klawiatury, takie jak CTRL + SHIFT + O, a nie SHIFT + klawisze CTRL + O, a zestaw <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0b062-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="0b062-126">Aby wyświetlić klucz dostępu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="0b062-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="0b062-127">Po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości polecenia menu, wprowadź handlowe "i" (&) przed literę, aby podkreślić, jak klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="0b062-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="0b062-128">Na przykład wpisanie `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości elementu menu spowoduje za pomocą polecenia menu, który jest wyświetlany jako <u>O</u>pióra.</span><span class="sxs-lookup"><span data-stu-id="0b062-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="0b062-129">Aby przejść do tego polecenia menu, naciśnij klawisz ALT, aby uaktywnić do <xref:System.Windows.Forms.MenuStrip>, a następnie naciśnij klawisz dostępu, nazwy menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="0b062-130">Jeśli menu zostanie otwarty i zawiera elementy z kluczami dostępu, wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b062-131">Unikaj definiowania zduplikowany klucz dostępu, takich jak definiowanie ALT + F dwa razy w tym samym systemie menu.</span><span class="sxs-lookup"><span data-stu-id="0b062-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="0b062-132">Nie można zagwarantować kolejność wybór zduplikowany klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="0b062-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="0b062-133">Aby wyświetlić pasek separatora między poleceń menu</span><span class="sxs-lookup"><span data-stu-id="0b062-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="0b062-134">Po zdefiniowaniu swoje <xref:System.Windows.Forms.MenuStrip> i będzie zawierać elementy użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> lub <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metodę, aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> mające na celu <xref:System.Windows.Forms.MenuStrip> w kolejności ma.</span><span class="sxs-lookup"><span data-stu-id="0b062-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b062-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b062-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="0b062-136">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="0b062-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
