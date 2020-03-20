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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Porady: dodawanie rozszerzeń do formantu ToolStripMenuItems
Użyteczność <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> kontrolki można zwiększyć w następujący sposób:  
  
- Dodaj znaczniki wyboru, aby określić, czy funkcja jest włączona czy wyłączona, na przykład czy linijka jest wyświetlana wzdłuż marginesu aplikacji edytora tekstu, lub aby wskazać, który plik na liście plików jest wyświetlany, na przykład w menu **Okno.**  
  
- Dodaj obrazy, które wizualnie reprezentują polecenia menu.  
  
- Wyświetlanie klawiszy skrótów w celu zapewnienia klawiatury alternatywnej dla myszy do wykonywania poleceń. Na przykład naciśnięcie klawiszy CTRL+C powoduje wykonanie polecenia **Kopiuj.**  
  
- Wyświetlanie klawiszy dostępu w celu zapewnienia klawiatury alternatywnej dla myszy do nawigacji po menu. Na przykład naciśnięcie klawiszy ALT+F powoduje wybranie menu **Plik.**  
  
- Pokaż paski separatora, aby pogrupować powiązane polecenia i uczynić menu bardziej czytelnymi.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Aby wyświetlić znacznik wyboru na poleceniu menu  
  
- Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> jego `true`właściwość na .  
  
     Spowoduje to <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> również `true`ustawienie właściwości na . Tej procedury należy używać tylko wtedy, gdy polecenie menu ma być domyślnie zaznaczone, niezależnie od tego, czy jest zaznaczone.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Aby wyświetlić znacznik wyboru, który zmienia stan przy każdym kliknięciu  
  
- Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość polecenia menu `true`na .  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Aby dodać obraz do polecenia menu  
  
- Ustaw <xref:System.Windows.Forms.ToolStripItem.Image%2A> właściwość polecenia menu na nazwę obrazu. Jeśli <xref:System.Windows.Forms.ToolStripItemDisplayStyle> właściwość tego polecenia menu <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>jest ustawiona na lub , obraz nie może być wyświetlany.  
  
> [!NOTE]
> Margines obrazu może również wyświetlać znacznik wyboru, jeśli tak zdecydujesz. Można również ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość obrazu `true`na , a obraz pojawi się z kreskowanym obramowaniem wokół niego w czasie wykonywania.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Aby wyświetlić klawisz skrótu dla polecenia menu  
  
- Ustaw właściwość polecenia <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> menu na żądaną kombinację klawiatury, taką jak CTRL+O `true`dla polecenia **Otwórz** menu, i ustaw właściwość na <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> .  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Aby wyświetlić niestandardowe klawisze skrótów dla polecenia menu  
  
- Ustaw właściwość polecenia <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> menu na żądaną kombinację klawiatury, taką jak CTRL+SHIFT+O, <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> a `true`nie SHIFT+CTRL+O, i ustaw właściwość na .  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Aby wyświetlić klawisz dostępu dla polecenia menu  
  
- Po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości dla polecenia menu wprowadź ampersand (&) przed literą, którą chcesz podkreślić jako klucz dostępu. Na przykład wpisanie <xref:System.Windows.Forms.ToolStripItem.Text%2A> jako właściwości elementu menu spowoduje wyświetlenie `&Open` polecenia menu wyświetlanego jako pióro <u>O.</u>
  
     Aby przejść do tego polecenia menu, naciśnij <xref:System.Windows.Forms.MenuStrip>klawisz ALT, aby skupić się na programie , a następnie naciśnij klawisz dostępu nazwy menu. Po otwarciu menu i pokazaniu elementów z klawiszami dostępu wystarczy nacisnąć klawisz dostępu, aby wybrać polecenie menu.  
  
> [!NOTE]
> Unikaj definiowania zduplikowanych klawiszy dostępu, takich jak dwukrotne definiowanie klawiszy ALT+F w tym samym systemie menu. Nie można zagwarantować kolejności wyboru zduplikowanych kluczy dostępu.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Aby wyświetlić pasek separatora między poleceniami menu  
  
- Po zdefiniowaniu <xref:System.Windows.Forms.MenuStrip> i elementy, które będą <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> zawierać, użyj lub metody, aby dodać polecenia menu i <xref:System.Windows.Forms.ToolStripSeparator> formanty do żądanej <xref:System.Windows.Forms.MenuStrip> kolejności.  
  
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

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip — Informacje o formancie](menustrip-control-overview-windows-forms.md)
