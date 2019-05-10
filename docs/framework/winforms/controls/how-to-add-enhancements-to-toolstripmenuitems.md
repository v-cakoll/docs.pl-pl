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
ms.openlocfilehash: 2aa2315667b34ac448ac34cd29402e39d59e79dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624098"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Instrukcje: dodawanie rozszerzeń do kontrolki ToolStripMenuItems
Możesz zwiększyć użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> kontrolek w następujący sposób:  
  
- Dodawanie znaczników zaznaczenia Określa, czy funkcja jest włączony lub wyłączony, takie jak czy linijki są wyświetlane wzdłuż marginesu edytora lub aby wskazać plik, który w postaci listy plików jest w trakcie wyświetlania, takich jak na **okna** menu.  
  
- Dodawanie obrazów, które wizualnie przedstawiają poleceń menu.  
  
- Wyświetlanie klawiszy skrótów, aby zapewnić klawiatury zamiast myszy do wykonywania poleceń. Na przykład, naciskając klawisze CTRL + C, wykonuje **kopiowania** polecenia.  
  
- Wyświetlanie kluczy dostępu do zapewnienia klawiatury zamiast myszy menu nawigacji. Na przykład, naciskając klawisze ALT + F wybiera **pliku** menu.  
  
- Wyświetlanie pasków separatorów grupować powiązane polecenia i zwiększyć czytelność menu.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Aby wyświetlić znacznik wyboru na poleceniu menu  
  
- Ustaw jego <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość `true`.  
  
     Powoduje ono również ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> właściwość `true`. Użyj tej procedury, tylko wtedy, gdy ma się wyświetlone jako zaznaczone domyślnie, niezależnie od tego, czy wybrano polecenie menu.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Aby wyświetlić znacznik wyboru, który zmienia stan każdego kliknięciem  
  
- Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Aby dodać obraz do polecenia menu  
  
- Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwość na nazwę obrazu. Jeśli <xref:System.Windows.Forms.ToolStripItemDisplayStyle> tego polecenia menu jest właściwością <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nie można wyświetlić obrazu.  
  
> [!NOTE]
>  Margines obrazka można również pokazać znacznik wyboru Jeśli więc wybrano. Ponadto można ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwości obrazu do `true`, a obraz pojawi się wraz z kreskowanym obramowaniem w czasie wykonywania.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Aby wyświetlić klawisza skrótu dla polecenia menu  
  
- Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> właściwości z kombinacją żądaną klawiatury, takie jak CTRL + O, aby uzyskać **Otwórz** polecenia menu, a następnie ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> właściwość `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Aby wyświetlić niestandardowe klawisze skrótu dla polecenia menu  
  
- Ustaw polecenie menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwości z kombinacją żądaną klawiatury, takie jak CTRL + SHIFT + O, a nie SHIFT + klawisze CTRL + O, a zestaw <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> właściwość `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Aby wyświetlić klucz dostępu dla polecenia menu  
  
- Po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości polecenia menu, wprowadź handlowe "i" (&) przed literę, aby podkreślić, jak klucz dostępu. Na przykład wpisanie `&Open` jako <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości elementu menu spowoduje za pomocą polecenia menu, który jest wyświetlany jako <u>O</u>pióra.
  
     Aby przejść do tego polecenia menu, naciśnij klawisz ALT, aby uaktywnić do <xref:System.Windows.Forms.MenuStrip>, a następnie naciśnij klawisz dostępu, nazwy menu. Jeśli menu zostanie otwarty i zawiera elementy z kluczami dostępu, wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.  
  
> [!NOTE]
>  Unikaj definiowania zduplikowany klucz dostępu, takich jak definiowanie ALT + F dwa razy w tym samym systemie menu. Nie można zagwarantować kolejność wybór zduplikowany klucz dostępu.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Aby wyświetlić pasek separatora między poleceń menu  
  
- Po zdefiniowaniu swoje <xref:System.Windows.Forms.MenuStrip> i będzie zawierać elementy użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> lub <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metodę, aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> mające na celu <xref:System.Windows.Forms.MenuStrip> w kolejności ma.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
