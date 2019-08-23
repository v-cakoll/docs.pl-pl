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
ms.openlocfilehash: 9e95c3623bf9bad8395f586392a0557ad1cde880
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912583"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="637ae-102">Instrukcje: dodawanie rozszerzeń do kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="637ae-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="637ae-103">Można zwiększyć użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> kontrolki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="637ae-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="637ae-104">Dodaj znaczniki wyboru, aby określić, czy funkcja jest włączona, czy wyłączona, na przykład czy wyświetlana jest linijka wzdłuż marginesu aplikacji do przetwarzania tekstu, czy też wskazuje, który plik jest wyświetlany na liście plików, na przykład w menu **okno** .</span><span class="sxs-lookup"><span data-stu-id="637ae-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="637ae-105">Dodaj obrazy, które wizualnie reprezentują polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="637ae-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="637ae-106">Wyświetlaj klawisze skrótów, aby zapewnić klawiaturę alternatywną dla myszy na potrzeby wykonywania poleceń.</span><span class="sxs-lookup"><span data-stu-id="637ae-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="637ae-107">Na przykład naciśnięcie klawiszy CTRL + C wykonuje polecenie **copy** .</span><span class="sxs-lookup"><span data-stu-id="637ae-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="637ae-108">Wyświetl klucze dostępu, aby zapewnić klawiaturę alternatywy dla myszy nawigacji menu.</span><span class="sxs-lookup"><span data-stu-id="637ae-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="637ae-109">Na przykład naciśnięcie klawiszy ALT + F wybiera menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="637ae-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="637ae-110">Pokaż paski separatorów, aby zgrupować powiązane polecenia i uczynić menu bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="637ae-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="637ae-111">Aby wyświetlić znacznik wyboru w menu polecenia</span><span class="sxs-lookup"><span data-stu-id="637ae-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="637ae-112">Ustaw jej <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="637ae-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="637ae-113">Spowoduje to również ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> właściwości na `true`.</span><span class="sxs-lookup"><span data-stu-id="637ae-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="637ae-114">Tej procedury należy użyć tylko wtedy, gdy chcesz, aby polecenie menu było wyświetlane jako zaznaczone domyślnie, niezależnie od tego, czy jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="637ae-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="637ae-115">Aby wyświetlić znacznik wyboru, który zmienia stan za pomocą każdego kliknięcia</span><span class="sxs-lookup"><span data-stu-id="637ae-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="637ae-116">Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość polecenia menu na `true`.</span><span class="sxs-lookup"><span data-stu-id="637ae-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="637ae-117">Aby dodać obraz do polecenia menu</span><span class="sxs-lookup"><span data-stu-id="637ae-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="637ae-118">Ustaw <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwość polecenia menu na nazwę obrazu.</span><span class="sxs-lookup"><span data-stu-id="637ae-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="637ae-119">Jeśli właściwość tego polecenia menu jest ustawiona na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nie można wyświetlić obrazu. <xref:System.Windows.Forms.ToolStripItemDisplayStyle></span><span class="sxs-lookup"><span data-stu-id="637ae-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="637ae-120">W przypadku wybrania tej opcji margines obrazu może również zawierać znacznik wyboru.</span><span class="sxs-lookup"><span data-stu-id="637ae-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="637ae-121">Ponadto można ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość obrazu na `true`, a obraz pojawi się z kreskowanym obramowaniem wokół niego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="637ae-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="637ae-122">Aby wyświetlić klawisz skrótu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="637ae-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="637ae-123">Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> właściwość polecenia menu na żądaną kombinację klawiatury, taką jak Ctrl + o dla polecenia **Otwórz** menu <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> , a następnie ustaw właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="637ae-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="637ae-124">Aby wyświetlić niestandardowe klawisze skrótów dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="637ae-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="637ae-125">Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwość polecenia menu na żądaną kombinację klawiatury, taką jak Ctrl + Shift + o, a nie Shift + Ctrl + O, a następnie <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> ustaw właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="637ae-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="637ae-126">Aby wyświetlić klucz dostępu dla polecenia menu</span><span class="sxs-lookup"><span data-stu-id="637ae-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="637ae-127">Po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości dla polecenia menu Wprowadź znak handlowego "i" (&) przed literą, która ma być podkreślona jako klucz dostępu.</span><span class="sxs-lookup"><span data-stu-id="637ae-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="637ae-128">Na przykład wpisywanie `&Open` <xref:System.Windows.Forms.ToolStripItem.Text%2A> jako właściwość elementu menu spowoduje polecenie menu, które pojawia się jako "pióro" <u></u>.</span><span class="sxs-lookup"><span data-stu-id="637ae-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="637ae-129">Aby przejść do tego polecenia menu, naciśnij klawisz Alt, aby ustawić fokus <xref:System.Windows.Forms.MenuStrip>, a następnie naciśnij klawisz dostępu nazwy menu.</span><span class="sxs-lookup"><span data-stu-id="637ae-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="637ae-130">Po otwarciu menu i wyświetleniu elementów z kluczami dostępu wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.</span><span class="sxs-lookup"><span data-stu-id="637ae-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="637ae-131">Należy unikać definiowania zduplikowanych kluczy dostępu, takich jak Definiowanie ALT + F dwa razy w tym samym systemie menu.</span><span class="sxs-lookup"><span data-stu-id="637ae-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="637ae-132">Nie można zagwarantować kolejności wyboru zduplikowanych kluczy dostępu.</span><span class="sxs-lookup"><span data-stu-id="637ae-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="637ae-133">Aby wyświetlić pasek separatora między poleceniami menu</span><span class="sxs-lookup"><span data-stu-id="637ae-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="637ae-134"><xref:System.Windows.Forms.MenuStrip> Po zdefiniowaniu i <xref:System.Windows.Forms.MenuStrip> zawartych w nim elementów należy <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> użyć metody lub <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> , aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> kontrolki w pożądanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="637ae-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="637ae-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="637ae-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="637ae-136">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="637ae-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
