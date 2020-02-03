---
title: Dodawanie i usuwanie kart za pomocą kontrolki TabControl
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 8292d8441f9b47334b98736cf3282c846673dbb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732721"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>Porady: dodawanie i usuwanie kart za pomocą formantu TabControl formularzy systemu Windows
Domyślnie formant <xref:System.Windows.Forms.TabControl> zawiera dwie kontrolki <xref:System.Windows.Forms.TabPage>. Dostęp do tych kart można uzyskać za pomocą właściwości <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
### <a name="to-add-a-tab-programmatically"></a>Aby programowo dodać kartę  
  
- Użyj metody <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> właściwości <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a>Aby programowo usunąć kartę  
  
- Aby usunąć wybrane karty, użyj metody <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> właściwości <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
     —lub—  
  
- Aby usunąć wszystkie karty, użyj metody <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> właściwości <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [TabControl, kontrolka — omówienie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: dodawanie kontrolki do karty](how-to-add-a-control-to-a-tab-page.md)
- [Instrukcje: wyłączanie kart](how-to-disable-tab-pages.md)
- [Instrukcje: zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
