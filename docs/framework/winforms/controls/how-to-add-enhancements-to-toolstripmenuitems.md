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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Instrukcje: dodawanie rozszerzeń do kontrolki ToolStripMenuItems
Można zwiększyć użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> kontrolki w następujący sposób:  
  
- Dodaj znaczniki wyboru, aby określić, czy funkcja jest włączona, czy wyłączona, na przykład czy wyświetlana jest linijka wzdłuż marginesu aplikacji do przetwarzania tekstu, czy też wskazuje, który plik jest wyświetlany na liście plików, na przykład w menu **okno** .  
  
- Dodaj obrazy, które wizualnie reprezentują polecenia menu.  
  
- Wyświetlaj klawisze skrótów, aby zapewnić klawiaturę alternatywną dla myszy na potrzeby wykonywania poleceń. Na przykład naciśnięcie klawiszy CTRL + C wykonuje polecenie **copy** .  
  
- Wyświetl klucze dostępu, aby zapewnić klawiaturę alternatywy dla myszy nawigacji menu. Na przykład naciśnięcie klawiszy ALT + F wybiera menu **plik** .  
  
- Pokaż paski separatorów, aby zgrupować powiązane polecenia i uczynić menu bardziej czytelne.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Aby wyświetlić znacznik wyboru w menu polecenia  
  
- Ustaw jej <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość na `true`.  
  
     Spowoduje to również ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> właściwości na `true`. Tej procedury należy użyć tylko wtedy, gdy chcesz, aby polecenie menu było wyświetlane jako zaznaczone domyślnie, niezależnie od tego, czy jest zaznaczone.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Aby wyświetlić znacznik wyboru, który zmienia stan za pomocą każdego kliknięcia  
  
- Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość polecenia menu na `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Aby dodać obraz do polecenia menu  
  
- Ustaw <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwość polecenia menu na nazwę obrazu. Jeśli właściwość tego polecenia menu jest ustawiona na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, nie można wyświetlić obrazu. <xref:System.Windows.Forms.ToolStripItemDisplayStyle>  
  
> [!NOTE]
> W przypadku wybrania tej opcji margines obrazu może również zawierać znacznik wyboru. Ponadto można ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość obrazu na `true`, a obraz pojawi się z kreskowanym obramowaniem wokół niego w czasie wykonywania.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Aby wyświetlić klawisz skrótu dla polecenia menu  
  
- Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> właściwość polecenia menu na żądaną kombinację klawiatury, taką jak Ctrl + o dla polecenia **Otwórz** menu <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> , a następnie ustaw właściwość na `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Aby wyświetlić niestandardowe klawisze skrótów dla polecenia menu  
  
- Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> właściwość polecenia menu na żądaną kombinację klawiatury, taką jak Ctrl + Shift + o, a nie Shift + Ctrl + O, a następnie <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> ustaw właściwość na `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Aby wyświetlić klucz dostępu dla polecenia menu  
  
- Po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości dla polecenia menu Wprowadź znak handlowego "i" (&) przed literą, która ma być podkreślona jako klucz dostępu. Na przykład wpisywanie `&Open` <xref:System.Windows.Forms.ToolStripItem.Text%2A> jako właściwość elementu menu spowoduje polecenie menu, które pojawia się jako "pióro" <u></u>.
  
     Aby przejść do tego polecenia menu, naciśnij klawisz Alt, aby ustawić fokus <xref:System.Windows.Forms.MenuStrip>, a następnie naciśnij klawisz dostępu nazwy menu. Po otwarciu menu i wyświetleniu elementów z kluczami dostępu wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.  
  
> [!NOTE]
> Należy unikać definiowania zduplikowanych kluczy dostępu, takich jak Definiowanie ALT + F dwa razy w tym samym systemie menu. Nie można zagwarantować kolejności wyboru zduplikowanych kluczy dostępu.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Aby wyświetlić pasek separatora między poleceniami menu  
  
- <xref:System.Windows.Forms.MenuStrip> Po zdefiniowaniu i <xref:System.Windows.Forms.MenuStrip> zawartych w nim elementów należy <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> użyć metody lub <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> , aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> kontrolki w pożądanej kolejności.  
  
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
