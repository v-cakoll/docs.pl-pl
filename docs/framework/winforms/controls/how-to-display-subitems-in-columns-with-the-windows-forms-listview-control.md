---
title: 'Porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows'
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
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać dodatkowy tekst lub podrzędnych, dla każdego elementu w widoku Details. Pierwsza kolumna Wyświetla tekst elementu, na przykład numer pracownika. Druga Strona, kolumny trzeci i kolejne zawierają pierwszy, drugi i kolejne skojarzone elementy podrzędne.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Aby dodać elementy podrzędne elementu listy  
  
1.  Dodawanie kolumn potrzebne. Ponieważ pierwszej kolumny spowoduje wyświetlenie elementu <xref:System.Windows.Forms.ListView.Text%2A> właściwość, należy jedną kolumnę więcej niż elementy podrzędne. Aby uzyskać więcej informacji na temat dodawania kolumny, zobacz [porady: Dodawanie kolumn do formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Wywołanie <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> metody kolekcji zwróconej przez <xref:System.Windows.Forms.ListViewItem.SubItems%2A> właściwości elementu. W poniższym przykładzie kodu ustawia nazwę pracowników i działu dla elementu listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Zobacz też  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
