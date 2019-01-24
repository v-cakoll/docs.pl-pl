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
ms.openlocfilehash: 1c58249df67efe5e782776d4996adef567f71a15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492212"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.ComboBox> formant jest używany do wyświetlania danych w polu kombi z listy rozwijanej. Domyślnie <xref:System.Windows.Forms.ComboBox> formantu pojawia się z dwóch części: górną część jest pola tekstowego, który umożliwia użytkownikowi na typ elementu listy. Druga część jest pole listy, który wyświetla listę elementów, z których użytkownik może wybrać jeden. Aby uzyskać więcej informacji na temat innych style pola kombi, zobacz [kiedy należy używać Windows Forms ComboBox Instead of ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Właściwość zwraca wartość całkowitą, która odnosi się do wybranego elementu listy. Wybrany element można programowo zmienić, zmieniając <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość w kodzie; odpowiedni element na liście pojawią się w polu tekstowym pola kombi. Jeśli żaden element nie jest zaznaczone, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość -1. Jeśli pierwszy element na liście jest zaznaczone, a następnie <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość jest równa 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Właściwości jest podobny do <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ale zwraca element, zazwyczaj wartość ciągu. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Właściwość odzwierciedla liczbę elementów na liście, a wartość <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> właściwości jest zawsze jeden więcej niż największa możliwa <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> jest liczony od zera.  
  
 Aby dodać lub usunąć elementy w <xref:System.Windows.Forms.ComboBox> kontrolować, należy użyć <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> metody. Alternatywnie, można dodać elementy do listy przy użyciu <xref:System.Windows.Forms.ComboBox.Items%2A> właściwość w projektancie.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ComboBox>
- [ListBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)
- [Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)
- [Instrukcje: Sortowanie zawartości Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Instrukcje: Uzyskiwanie dostępu do określonych elementów w Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Instrukcje: Powiąż Windows Forms kontrolki ComboBox lub ListBox z danymi](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
- [Instrukcje: Tworzenie tabeli wyszukiwania dla Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
