---
title: Dodawanie i usuwanie kart za pomocą kontrolki TabControl
description: Dowiedz się, jak dodawać i usuwać karty z Windows Forms kontrolką TabControl, która zawiera dwie kontrolki TabPage. Uzyskaj dostęp do tych kart za pomocą właściwości TabPages.
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
ms.openlocfilehash: 7e67d0bbc13bd7d9c8835dc6fb9b9c5c9333b8bf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618080"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>Porady: dodawanie i usuwanie kart za pomocą formantu TabControl formularzy systemu Windows
Domyślnie <xref:System.Windows.Forms.TabControl> kontrolka zawiera dwie <xref:System.Windows.Forms.TabPage> kontrolki. Dostęp do tych kart można uzyskać za pomocą <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości.  
  
### <a name="to-add-a-tab-programmatically"></a>Aby programowo dodać kartę  
  
- Użyj <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> metody <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości.  
  
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
  
- Aby usunąć wybrane karty, użyj <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> metody <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości.  
  
     -lub-  
  
- Aby usunąć wszystkie karty, użyj <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> metody <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości.  
  
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

- [TabControl — Informacje o formancie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: dodawanie kontrolki do karty](how-to-add-a-control-to-a-tab-page.md)
- [Porady: wyłączanie kart](how-to-disable-tab-pages.md)
- [Porady: zmienianie wyglądu składnika TabControl formularzy systemu Windows](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
