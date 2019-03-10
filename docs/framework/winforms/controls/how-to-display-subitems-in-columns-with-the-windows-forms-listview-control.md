---
title: 'Instrukcje: Wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy Windows'
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
ms.openlocfilehash: ecdb16087ff5788723b7d562cebd08551df87deb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713075"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Instrukcje: Wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy Windows
Formularze Windows <xref:System.Windows.Forms.ListView> formant może wyświetlić dodatkowy tekst lub podrzędnych dla każdego elementu w widoku szczegółów. Pierwsza kolumna Wyświetla tekst elementu, na przykład numer pracownika. Drugi, trzeci i kolejnych kolumn wyświetlany jako pierwszy, drugi i kolejne skojarzone elementy podrzędne.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Aby dodać elementy podrzędne elementu listy  
  
1.  Dodaj potrzebne kolumny. Ponieważ pierwszej kolumny spowoduje wyświetlenie elementu <xref:System.Windows.Forms.ListView.Text%2A> właściwość, należy jedną kolumnę więcej niż elementy podrzędne. Aby uzyskać więcej informacji na temat dodawania kolumn, zobacz [jak: Dodawanie kolumn do Windows formantu ListView formularzy](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Wywołaj <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metoda zbiorze zwróconym przez <xref:System.Windows.Forms.ListViewItem.SubItems%2A> właściwości elementu. Poniższy przykładowy kod ustawia nazwiska pracownika i działu dla elementu listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Zobacz także
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie ikon dla kontrolki ListView formularzy Windows](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
