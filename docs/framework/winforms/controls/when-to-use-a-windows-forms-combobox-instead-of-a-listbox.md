---
title: ComboBox a ListBox
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
ms.openlocfilehash: 7087760a393bb58d83d899c1741c745fb28585bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739928"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
<xref:System.Windows.Forms.ComboBox> i kontrolki <xref:System.Windows.Forms.ListBox> mają podobne zachowania, a w niektórych przypadkach mogą być zamienne. Istnieją jednak przypadki, gdy jedna lub druga jest bardziej odpowiednia dla zadania.  
  
 Ogólnie rzecz biorąc, pole kombi jest odpowiednie, gdy istnieje lista sugerowanych opcji, a pole listy jest odpowiednie, gdy chcesz ograniczyć dane wejściowe do listy. Pole kombi zawiera pole tekstowe, dlatego wybory, które nie znajdują się na liście, można wpisać w. Wyjątek występuje, gdy właściwość <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. W takim przypadku kontrolka wybierze element w przypadku wpisania jego pierwszej litery.  
  
 Ponadto pola kombi oszczędzają miejsce w formularzu. Ponieważ pełna lista nie jest wyświetlana, dopóki użytkownik nie kliknie strzałkę w dół, pole kombi może łatwo zmieścić się w niewielkim miejscu, w którym pole listy nie zmieści się. Wyjątek polega na tym, że właściwość <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: wyświetlana jest pełna lista, a pole kombi zajmuje więcej miejsca niż pole listy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Instrukcje: sortowanie zawartości kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
