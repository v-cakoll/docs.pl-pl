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
ms.openlocfilehash: 37843d27211bd07c2749b3e6fc14ec03d7bf570d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Porady: dodawanie rozszerzeń do formantu ToolStripMenuItems
Może poprawić użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> formanty w następujący sposób:  
  
-   Dodawanie znaczników zaznaczenia Określa, czy funkcja jest włączony czy wyłączony, takie jak czy linijki jest wyświetlane wzdłuż marginesu edytora lub aby wskazać, który plik na liście plików jest w trakcie wyświetlania, na przykład na dzień **okna** menu.  
  
-   Dodawanie obrazów, które wizualnie reprezentują poleceń menu.  
  
-   Wyświetlanie klawiszy skrótów do zapewnienia klawiatury sposobem myszy wykonywania poleceń. Na przykład, naciskając klawisze CTRL + C wykonuje **kopiowania** polecenia.  
  
-   Wyświetl klucze dostępu zapewnienie klawiatury sposobem myszy menu nawigacji. Na przykład, naciskając klawisze ALT + F wybierze **pliku** menu.  
  
-   Wyświetlanie pasków separatorów do grupowania powiązanych poleceń i odczytywać menu.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Aby wyświetlić znacznik wyboru polecenia menu  
  
-   Ustaw jego <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwości `true`.  
  
     Powoduje ono również ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> właściwości `true`. Użyj tej procedury, tylko wtedy, gdy ma się pojawiają się jako zaznaczone domyślnie, niezależnie od tego, czy jest wybrane polecenie menu.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Aby wyświetlić znacznik wyboru, który zmienia stan każdego kliknięciem  
  
-   Polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwości `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Aby dodać obraz do polecenia menu  
  
-   Polecenie menu <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwości do nazwy obrazu. Jeśli <xref:System.Windows.Forms.ToolStripItemDisplayStyle> ma ustawioną właściwość tego polecenia menu <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nie można wyświetlić obrazu.  
  
> [!NOTE]
>  Margines obrazu może także wyświetlać znacznik wyboru po należy więc wybrać. Ponadto można ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwości obrazu do `true`, a obraz pojawi się wraz z kreskowanym obramowaniem w czasie wykonywania.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Aby wyświetlić klawisz skrótu polecenia menu  
  
-   Polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> właściwości kombinację żądaną klawiatury, np. CTRL + O, dla **Otwórz** polecenia menu i ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> właściwości `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Aby wyświetlić niestandardowe klawisze skrótu dla polecenia menu  
  
-   Polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwości kombinację żądaną klawiatury, np. CTRL + SHIFT + O, a nie SHIFT + CTRL + O, a zestaw <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> właściwości `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Aby wyświetlić klucz dostępu dla polecenia menu  
  
-   Podczas ustawiania <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość polecenia menu, wprowadź handlowego "i" (&) przed literą, aby podkreślić, jak klucz dostępu. Na przykład wpisanie `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości elementu menu spowoduje polecenia menu, który jest wyświetlany jako **O**pióra.  
  
     Aby przejść do tego polecenia menu, naciśnij klawisz ALT, aby uaktywnić do <xref:System.Windows.Forms.MenuStrip>, a następnie naciśnij klawisz dostępu nazwy menu. Jeśli menu zostanie otwarty i zawiera elementy z klawiszy dostępu, wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.  
  
> [!NOTE]
>  Unikaj definiowania klucze dostępu duplikatów, takie jak definiowanie ALT + F dwa razy w tym samym systemie menu. Nie można zagwarantować kolejność wyboru dostępu zduplikowane klucze.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Aby wyświetlić pasek separatora między poleceń menu  
  
-   Po zdefiniowaniu Twojej <xref:System.Windows.Forms.MenuStrip> i będzie zawierać elementy użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> lub <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metodę, aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> formanty <xref:System.Windows.Forms.MenuStrip> w dowolnej kolejności.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
