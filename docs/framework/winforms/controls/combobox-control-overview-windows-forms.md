---
title: ComboBox, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 9fb270d7787902872a32a87c140316f756bd48aa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743848"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox — Informacje o formancie [Formularze systemu Windows]
Formant Windows Forms <xref:System.Windows.Forms.ComboBox> służy do wyświetlania danych w rozwijanym polu kombi. Domyślnie formant <xref:System.Windows.Forms.ComboBox> pojawia się w dwóch częściach: górną częścią jest pole tekstowe, które umożliwia użytkownikowi wpisanie elementu listy. Druga część to pole listy, w którym jest wyświetlana lista elementów, z których użytkownik może ją wybrać. Aby uzyskać więcej informacji na temat innych stylów pola kombi, zobacz [Kiedy używać Windows Forms ComboBox zamiast elementu ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 Właściwość <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> zwraca liczbę całkowitą, która odpowiada wybranemu elementowi listy. Można programowo zmienić wybrany element, zmieniając wartość <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> w kodzie; odpowiadający element na liście pojawi się w polu tekstowym pola kombi. Jeśli nie wybrano żadnego elementu, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartość-1. W przypadku wybrania pierwszego elementu na liście wartość <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wynosi 0. Właściwość <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> jest podobna do <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, ale zwraca sam element, zazwyczaj wartość ciągu. Właściwość <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> odzwierciedla liczbę elementów na liście, a wartość właściwości <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> jest zawsze większa od największej możliwej <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> wartości, ponieważ <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> jest oparta na zero.  
  
 Aby dodać lub usunąć elementy w kontrolce <xref:System.Windows.Forms.ComboBox>, użyj metody <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> lub <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>. Alternatywnie można dodać elementy do listy za pomocą właściwości <xref:System.Windows.Forms.ComboBox.Items%2A> w projektancie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ComboBox>
- [ListBox, kontrolka — omówienie](listbox-control-overview-windows-forms.md)
- [Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Instrukcje: sortowanie zawartości kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Instrukcje: uzyskiwanie dostępu do określonych elementów w kontrolkach ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Instrukcje: wiązanie kontrolki ComboBox lub ListBox (Windows Forms) z danymi](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
- [Instrukcje: tworzenie tabeli wyszukiwania dla kontrolek ComboBox, ListBox i CheckedListBox formularzy Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
