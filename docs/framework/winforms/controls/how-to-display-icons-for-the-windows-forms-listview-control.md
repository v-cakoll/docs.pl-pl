---
title: 'Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy systemu Windows'
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
ms.openlocfilehash: 8e4ae744eecbe894767114179dd63651828b191b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013442"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać ikony z trzema list obrazów. Widoki List, szczegóły i SmallIcon wyświetlanie obrazów z listy obrazów, określone w <xref:System.Windows.Forms.ListView.SmallImageList%2A> właściwości. Wyświetl LargeIcon wyświetla obrazy z listy obrazów, określone w <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości. Widok listy można także wyświetlać dodatkowego zestawu ikon w <xref:System.Windows.Forms.ListView.StateImageList%2A> właściwości obok duże lub małe ikony. Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](imagelist-component-windows-forms.md) i [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Aby wyświetlić obrazy w widoku listy  
  
1. Ustawić właściwość odpowiednie —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, lub <xref:System.Windows.Forms.ListView.StateImageList%2A>— do istniejącego <xref:System.Windows.Forms.ImageList> składników, które chcesz użyć.  
  
     Te właściwości można ustawić w projektancie w oknie właściwości lub w kodzie.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. Ustaw <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> lub <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> właściwości dla każdego elementu listy, który zawiera ikonę skojarzone.  
  
     Te właściwości można ustawić w kodzie lub w ramach **ListViewItem — Edytor kolekcji**. Aby otworzyć **ListViewItem — Edytor kolekcji**, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok <xref:System.Windows.Forms.ListView.Items%2A>właściwość **właściwości** okna.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList, składnik](imagelist-component-windows-forms.md)
