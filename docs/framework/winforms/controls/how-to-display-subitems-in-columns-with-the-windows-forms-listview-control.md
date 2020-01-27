---
title: Wyświetlanie elementów SubItems w kolumnach z kontrolką ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745547"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać dodatkowy tekst lub podelementy dla każdego elementu w widoku szczegółów. W pierwszej kolumnie jest wyświetlany tekst elementu, na przykład numer pracownika. Druga, trzecia i kolejne kolumny wyświetlają pierwszy, drugi i kolejne skojarzone elementy.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Aby dodać elementy podelementowe do elementu listy  
  
1. Dodaj wszystkie potrzebne kolumny. Ponieważ w pierwszej kolumnie będzie wyświetlana właściwość <xref:System.Windows.Forms.ListView.Text%2A> elementu, potrzebna jest jeszcze jedna kolumna niż w przypadku elementów SubItems. Aby uzyskać więcej informacji na temat dodawania kolumn, zobacz [jak to zrobić: Dodawanie kolumn do kontrolki ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Wywołaj metodę <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> kolekcji zwróconej przez właściwość <xref:System.Windows.Forms.ListViewItem.SubItems%2A> elementu. Poniższy przykład kodu ustawia nazwę pracownika i dział dla elementu listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
