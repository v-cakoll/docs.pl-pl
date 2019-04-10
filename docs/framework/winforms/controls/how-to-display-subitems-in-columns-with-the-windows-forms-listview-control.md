---
title: 'Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy systemu Windows'
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
ms.openlocfilehash: 318521cc1377be89ef54706d80c8b2990a6ba1b8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339297"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.ListView> formant może wyświetlić dodatkowy tekst lub podrzędnych dla każdego elementu w widoku szczegółów. Pierwsza kolumna Wyświetla tekst elementu, na przykład numer pracownika. Drugi, trzeci i kolejnych kolumn wyświetlany jako pierwszy, drugi i kolejne skojarzone elementy podrzędne.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Aby dodać elementy podrzędne elementu listy  
  
1. Dodaj potrzebne kolumny. Ponieważ pierwszej kolumny spowoduje wyświetlenie elementu <xref:System.Windows.Forms.ListView.Text%2A> właściwość, należy jedną kolumnę więcej niż elementy podrzędne. Aby uzyskać więcej informacji na temat dodawania kolumn, zobacz [jak: Dodawanie kolumn do Windows formantu ListView formularzy](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Wywołaj <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda zbiorze zwróconym przez <xref:System.Windows.Forms.ListViewItem.SubItems%2A> właściwości elementu. Poniższy przykładowy kod ustawia nazwiska pracownika i działu dla elementu listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy systemu Windows](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Formularze systemu Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
