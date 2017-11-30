---
title: "Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d9a8bdc54f3f321b37bda897aac1f340f7a46aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać ikony z trzech list obrazów. Widoki List, szczegóły i SmallIcon wyświetlanie obrazów z listy obrazów, określona w <xref:System.Windows.Forms.ListView.SmallImageList%2A> właściwości. W widoku LargeIcon wyświetlane obrazów z listy obrazów, określona w <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości. Widok listy można również wyświetlić dodatkowe zbiór ikony w <xref:System.Windows.Forms.ListView.StateImageList%2A> właściwości obok duże lub małe ikony. Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) i [porady: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### <a name="to-display-images-in-a-list-view"></a>Do wyświetlania obrazów w widoku listy  
  
1.  Ustaw odpowiednie właściwości —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, lub <xref:System.Windows.Forms.ListView.StateImageList%2A>— do istniejącej <xref:System.Windows.Forms.ImageList> składników, które chcesz użyć.  
  
     Te właściwości można ustawić w projektancie w oknie właściwości lub w kodzie.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  Ustaw <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> lub <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> właściwości dla każdego elementu listy, który ma skojarzona ikona.  
  
     Te właściwości można ustawić kodu lub poziomu **edytora kolekcji ListViewItem**. Aby otworzyć **edytora kolekcji ListViewItem**, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok <xref:System.Windows.Forms.ListView.Items%2A>właściwość **właściwości** okna.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o formancie ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Porady: Dodawanie i usuwanie elementów za pomocą systemu Windows formantu ListView formularzy](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Porady: Dodawanie kolumn do systemu Windows formantu ListView formularzy](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Porady: Dodawanie niestandardowych informacji do formantu TreeView lub ListView (formularze systemu Windows)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [ImageList — składnik](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
