---
title: "ComboBox — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 979a410020ab6e3a1f2c15dcee52b062eb00c1ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.ComboBox> formant jest używana do wyświetlania danych w polu kombi listy rozwijanej. Domyślnie <xref:System.Windows.Forms.ComboBox> formant jest widoczny w dwóch częściach: górnej części jest polem tekstowym, który zezwala użytkownikowi na typ elementu listy. Druga część to pole listy, które wyświetla listę elementów, z których użytkownik może wybrać jeden. Aby uzyskać więcej informacji dotyczących innych style pola kombi, zobacz [kiedy należy używać systemu Windows Forms ComboBox Instead of ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Właściwość zwraca wartość całkowitą, która odpowiada do wybranego elementu listy. Wybrany element można programowo zmienić, zmieniając <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartości w kodzie; odpowiadający mu element na liście będą wyświetlane w polu tekstowym pola kombi. Jeśli nie wybrano elementów, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość wynosi -1. Jeśli wybrano pierwszy element na liście, a następnie <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość jest równa 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Jest podobna do właściwości <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ale zwraca sam element zwykle wartość ciągu. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Właściwość odzwierciedla liczbę elementów na liście, a wartość <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> właściwości jest zawsze jeden więcej niż największa możliwa <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> jest liczony od zera.  
  
 Aby dodać lub usunąć elementy <xref:System.Windows.Forms.ComboBox> kontrolować, użyj <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> metody. Można również dodać elementy do listy przy użyciu <xref:System.Windows.Forms.ComboBox.Items%2A> właściwości w projektancie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ComboBox>  
 [Informacje o formancie ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [Porady: Dodawanie i usuwanie elementów z systemu Windows formularzy ComboBox, ListBox lub CheckedListBox — formant](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Porady: sortowanie zawartości systemu Windows ComboBox, ListBox lub CheckedListBox formularzy](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Porady: uzyskiwanie dostępu do określonych elementów w systemie Windows formularzy ComboBox, ListBox lub CheckedListBox — formant](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [Porady: powiązanie formantu ComboBox formularzy systemu Windows lub kontrolki ListBox z danymi](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Formanty używane do obsługi opcji List formularzy systemu Windows](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Porady: Tworzenie tabeli wyszukiwania dla formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
