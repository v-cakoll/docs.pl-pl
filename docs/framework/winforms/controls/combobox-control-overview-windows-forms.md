---
title: ComboBox — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: c8cd0430e9abaed0ee58e971edf6a9c871da37c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527394"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.ComboBox> formant jest używana do wyświetlania danych w polu kombi listy rozwijanej. Domyślnie <xref:System.Windows.Forms.ComboBox> formant jest widoczny w dwóch częściach: górnej części jest polem tekstowym, który zezwala użytkownikowi na typ elementu listy. Druga część to pole listy, które wyświetla listę elementów, z których użytkownik może wybrać jeden. Aby uzyskać więcej informacji dotyczących innych style pola kombi, zobacz [kiedy należy używać systemu Windows Forms ComboBox Instead of ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Właściwość zwraca wartość całkowitą, która odpowiada do wybranego elementu listy. Wybrany element można programowo zmienić, zmieniając <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartości w kodzie; odpowiadający mu element na liście będą wyświetlane w polu tekstowym pola kombi. Jeśli nie wybrano elementów, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość wynosi -1. Jeśli wybrano pierwszy element na liście, a następnie <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość jest równa 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Jest podobna do właściwości <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ale zwraca sam element zwykle wartość ciągu. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Właściwość odzwierciedla liczbę elementów na liście, a wartość <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> właściwości jest zawsze jeden więcej niż największa możliwa <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> jest liczony od zera.  
  
 Aby dodać lub usunąć elementy <xref:System.Windows.Forms.ComboBox> kontrolować, użyj <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> metody. Można również dodać elementy do listy przy użyciu <xref:System.Windows.Forms.ComboBox.Items%2A> właściwości w projektancie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ComboBox>  
 [ListBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Instrukcje: sortowanie zawartości kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Instrukcje: uzyskiwanie dostępu do określonych elementów w kontrolkach ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [Instrukcje: wiązanie kontrolki ComboBox lub ListBox (Windows Forms) z danymi](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Instrukcje: tworzenie tabeli wyszukiwania dla kontrolek ComboBox, ListBox i CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
