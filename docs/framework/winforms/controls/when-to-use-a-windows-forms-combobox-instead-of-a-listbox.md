---
title: ComboBox a ListBox
description: Dowiedz się więcej o używaniu Windows Forms ComboBox i Windows Forms ListBox i Dowiedz się, jak określić, kiedy jedna lub druga jest bardziej odpowiednia dla zadania.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174422"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
<xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> Formanty i mają podobne zachowania, a w niektórych przypadkach mogą być zamienne. Istnieją jednak przypadki, gdy jedna lub druga jest bardziej odpowiednia dla zadania.  
  
 Ogólnie rzecz biorąc, pole kombi jest odpowiednie, gdy istnieje lista sugerowanych opcji, a pole listy jest odpowiednie, gdy chcesz ograniczyć dane wejściowe do listy. Pole kombi zawiera pole tekstowe, dlatego wybory, które nie znajdują się na liście, można wpisać w. Wyjątek występuje, gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> Właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> . W takim przypadku kontrolka wybierze element w przypadku wpisania jego pierwszej litery.  
  
 Ponadto pola kombi oszczędzają miejsce w formularzu. Ponieważ pełna lista nie jest wyświetlana, dopóki użytkownik nie kliknie strzałkę w dół, pole kombi może łatwo zmieścić się w niewielkim miejscu, w którym pole listy nie zmieści się. Wyjątek występuje <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> , gdy właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple> : wyświetlana jest pełna lista, a pole kombi zajmuje więcej miejsca niż pole listy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Porady: dodawanie i usuwanie elementów za pomocą formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows](add-and-remove-items-from-a-wf-combobox.md)
- [Porady: sortowanie zawartości formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Formanty formularzy systemu Windows używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)
