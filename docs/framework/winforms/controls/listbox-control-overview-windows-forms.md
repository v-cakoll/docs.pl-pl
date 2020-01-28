---
title: ListBox — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 1abf8bea5c786f2ce326631370fa294ada09a92c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745183"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.ListBox> Windows Forms wyświetla listę, z której użytkownik może wybrać jeden lub więcej elementów. Jeśli całkowita liczba elementów przekracza liczbę, która może być wyświetlana, pasek przewijania jest automatycznie dodawany do kontrolki <xref:System.Windows.Forms.ListBox>. Gdy właściwość <xref:System.Windows.Forms.ListBox.MultiColumn%2A> jest ustawiona na `true`, w polu listy są wyświetlane elementy z wielu kolumn i zostanie wyświetlony poziomy pasek przewijania. Gdy właściwość <xref:System.Windows.Forms.ListBox.MultiColumn%2A> jest ustawiona na `false`, pole listy wyświetla elementy w jednej kolumnie, a widoczny jest pionowy pasek przewijania. Gdy <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> jest ustawiona na `true`, pasek przewijania pojawia się niezależnie od liczby elementów. Właściwość <xref:System.Windows.Forms.ListBox.SelectionMode%2A> określa, ile elementów listy można wybrać w danym momencie.  
  
## <a name="ways-to-change-the-listbox-control"></a>Sposoby zmiany formantu ListBox  
 Właściwość <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> zwraca liczbę całkowitą, która odnosi się do pierwszego wybranego elementu w polu listy. Można programowo zmienić wybrany element, zmieniając wartość <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> w kodzie; odpowiadający element na liście zostanie wyróżniony w formularzu systemu Windows. Jeśli nie wybrano żadnego elementu, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość-1. W przypadku wybrania pierwszego elementu na liście wartość <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wynosi 0. W przypadku wybrania wielu elementów <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartość odzwierciedla wybrany element, który pojawia się jako pierwszy na liście. Właściwość <xref:System.Windows.Forms.ListBox.SelectedItem%2A> jest podobna do <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale zwraca sam element, zazwyczaj wartość ciągu. Właściwość <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> odzwierciedla liczbę elementów na liście, a wartość właściwości <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> jest zawsze większa od największej możliwej <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> jest oparta na zero.  
  
 Aby dodać lub usunąć elementy w kontrolce <xref:System.Windows.Forms.ListBox>, użyj metody <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>. Alternatywnie możesz dodać elementy do listy przy użyciu właściwości <xref:System.Windows.Forms.ListBox.Items%2A> w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListBox>
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Instrukcje: sortowanie zawartości kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Instrukcje: wiązanie kontrolki ComboBox lub ListBox (Windows Forms) z danymi](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox, kontrolka — omówienie](combobox-control-overview-windows-forms.md)
- [CheckedListBox, kontrolka — omówienie](checkedlistbox-control-overview-windows-forms.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
- [Instrukcje: tworzenie tabeli wyszukiwania dla kontrolek ComboBox, ListBox i CheckedListBox formularzy Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
