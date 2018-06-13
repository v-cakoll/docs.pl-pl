---
title: ListBox — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: d4cb423a6f32778695abeae725da9755b610d209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537567"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.ListBox> kontrolka ma wyświetlać listę, z którego użytkownik może wybrać co najmniej jeden element. Jeśli całkowita liczba elementów przekracza liczbę, która może być wyświetlana, pasek przewijania jest automatycznie dodawany do <xref:System.Windows.Forms.ListBox> formantu. Gdy <xref:System.Windows.Forms.ListBox.MultiColumn%2A> właściwość jest ustawiona na `true`, elementy w polu listy są wyświetlane w wielu kolumnach i zostanie wyświetlony pasek przewijania poziomego. Gdy <xref:System.Windows.Forms.ListBox.MultiColumn%2A> właściwość jest ustawiona na `false`, elementy w polu listy są wyświetlane w jednej kolumnie i jest wyświetlany pionowy pasek przewijania. Gdy <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> ma ustawioną wartość `true`, zostanie wyświetlony pasek przewijania, niezależnie od liczby elementów. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Właściwość określa, ile elementów listy można wybrać w czasie.  
  
## <a name="ways-to-change-the-listbox-control"></a>Sposoby zmiany ListBox — formant  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Właściwość zwraca wartość całkowitą, która odpowiada do pierwszego elementu zaznaczonego w polu listy. Wybrany element można programowo zmienić, zmieniając <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartości w kodzie; odpowiadający mu element na liście będą wyświetlane wyróżnione na formularzu systemu Windows. Jeśli nie wybrano elementów, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość wynosi -1. Jeśli wybrano pierwszy element na liście, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość jest równa 0. Po wybraniu wielu elementów <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość odzwierciedla wybranego elementu, który znajduje się na liście. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Jest podobna do właściwości <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale zwraca sam element zwykle wartość ciągu. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Właściwość odzwierciedla liczbę elementów na liście, a wartość <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> właściwości jest zawsze jeden więcej niż największa możliwa <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> jest liczony od zera.  
  
 Aby dodać lub usunąć elementy <xref:System.Windows.Forms.ListBox> kontrolować, użyj <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> metody. Można również dodać elementy do listy przy użyciu <xref:System.Windows.Forms.ListBox.Items%2A> właściwości w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListBox>  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Instrukcje: sortowanie zawartości kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Instrukcje: wiązanie kontrolki ComboBox lub ListBox (Windows Forms) z danymi](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [ComboBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Instrukcje: tworzenie tabeli wyszukiwania dla kontrolek ComboBox, ListBox i CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
