---
title: Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: e6cdc7f0d54d54448a7b9ed42603b07c93eba719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668343"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
<xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> kontrolki mają podobne zachowania, a w niektórych przypadkach może być wymienne. Brak sytuacji, gdy jednej z nich jest bardziej odpowiednie do zadania.  
  
 Ogólnie rzecz biorąc pola kombi jest odpowiednie, jeśli znajduje się lista sugerowanych dostępnych opcji i pola listy jest odpowiednia w przypadku, gdy chcesz ograniczyć dane wejściowe, co znajduje się na liście. Pole kombi zawiera pole tekstowe, więc wpisano opcji nie ma na liście. Wyjątkiem jest, gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. W takim przypadku formantu wybierz element, jeśli wpiszesz swojej pierwszej litery.  
  
 Ponadto pola kombi zaoszczędzić miejsce na formularzu. Ponieważ pełnej listy nie jest wyświetlany, dopóki użytkownik kliknie strzałkę w dół, pola kombi mogą łatwo mieści się w mała ilość miejsca, gdzie pole listy nie pasuje. Wyjątek jest, gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: wyświetlana jest pełna lista i pola kombi zajmuje więcej miejsca niż będzie pola listy.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)
- [Instrukcje: Sortowanie zawartości Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
