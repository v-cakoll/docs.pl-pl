---
title: ListBox — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 2bba90f704458e1c724328feccaaf6f04b98ecb4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723988"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.ListBox> kontrolka Wyświetla listę, z którego użytkownik może wybrać co najmniej jeden element. Jeśli łączna liczba elementów przekracza liczbę, która może być wyświetlana, pasek przewijania jest automatycznie dodawany do <xref:System.Windows.Forms.ListBox> kontroli. Gdy <xref:System.Windows.Forms.ListBox.MultiColumn%2A> właściwość jest ustawiona na `true`, elementy w polu listy są wyświetlane w wielu kolumnach i zostanie wyświetlony pasek przewijania poziomego. Gdy <xref:System.Windows.Forms.ListBox.MultiColumn%2A> właściwość jest ustawiona na `false`, elementy w polu listy są wyświetlane w jednej kolumnie, i zostanie wyświetlony pasek przewijania pionowego. Gdy <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> ustawiono `true`, niezależnie od liczby elementów zostanie wyświetlony pasek przewijania. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Właściwość określa, ile elementów listy można wybrać w danym momencie.  
  
## <a name="ways-to-change-the-listbox-control"></a>Sposoby zmiany ListBox, kontrolka  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Właściwość zwraca wartość całkowitą, która odnosi się do pierwszego elementu wybranego w polu listy. Wybrany element można programowo zmienić, zmieniając <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość w kodzie; zostanie wyróżniony odpowiedni element na liście w formularzu Windows. Jeśli żaden element nie jest zaznaczone, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość -1. Jeśli pierwszy element na liście jest zaznaczone, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość jest równa 0. Po wybraniu wielu elementów <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość odzwierciedla wybranego elementu, który znajduje się na liście. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Właściwości jest podobny do <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale zwraca element, zazwyczaj wartość ciągu. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Właściwość odzwierciedla liczbę elementów na liście, a wartość <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> właściwości jest zawsze jeden więcej niż największa możliwa <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> jest liczony od zera.  
  
 Aby dodać lub usunąć elementy w <xref:System.Windows.Forms.ListBox> kontrolować, należy użyć <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> metody. Alternatywnie, można dodać elementy do listy przy użyciu <xref:System.Windows.Forms.ListBox.Items%2A> właściwości w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ListBox>
- [Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](add-and-remove-items-from-a-wf-combobox.md)
- [Instrukcje: Sortowanie zawartości Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Instrukcje: Powiąż Windows Forms kontrolki ComboBox lub ListBox z danymi](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox, kontrolka — omówienie](combobox-control-overview-windows-forms.md)
- [CheckedListBox, kontrolka — omówienie](checkedlistbox-control-overview-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
- [Instrukcje: Tworzenie tabeli wyszukiwania dla Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](create-a-lookup-table-for-a-wf-combobox-listbox.md)
