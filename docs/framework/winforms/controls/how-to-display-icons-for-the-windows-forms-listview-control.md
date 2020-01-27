---
title: Wyświetl ikony dla kontrolki ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744505"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać ikony z trzech list obrazów. Widoki list, szczegółów i SmallIcon wyświetlają obrazy z listy obrazów określonych we właściwości <xref:System.Windows.Forms.ListView.SmallImageList%2A>. Widok widoku LargeIcon wyświetla obrazy z listy obrazów określony we właściwości <xref:System.Windows.Forms.ListView.LargeImageList%2A>. W widoku listy można także wyświetlić dodatkowy zestaw ikon ustawionych we właściwości <xref:System.Windows.Forms.ListView.StateImageList%2A> obok wielkich lub małych ikon. Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Aby wyświetlić obrazy w widoku listy  
  
1. Ustaw odpowiednią właściwość —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>lub <xref:System.Windows.Forms.ListView.StateImageList%2A>— na istniejący składnik <xref:System.Windows.Forms.ImageList>, którego chcesz użyć.  
  
     Te właściwości można ustawić w projektancie przy użyciu okno Właściwości lub w kodzie.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. Ustaw właściwość <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> lub <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> dla każdego elementu listy, który ma skojarzoną ikonę.  
  
     Te właściwości można ustawić w kodzie lub w **edytorze kolekcji ListViewItem**. Aby otworzyć **Edytor kolekcji ListViewItem**, kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Items%2A> w oknie **Właściwości** .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList, składnik](imagelist-component-windows-forms.md)
