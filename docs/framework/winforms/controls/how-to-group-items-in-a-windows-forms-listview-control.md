---
title: Grupuj elementy w formancie ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736626"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Porady: grupowanie elementów w formancie ListView formularzy systemu Windows
Za pomocą funkcji grupowania kontrolki <xref:System.Windows.Forms.ListView> można wyświetlić powiązane zestawy elementów w grupach. Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup. Korzystając z grup <xref:System.Windows.Forms.ListView>, można ułatwić nawigację dużych list, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne. Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy.  
  
 ![Zrzut ekranu przedstawiający nieparzystą i parzystą grupę ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w projektancie lub programowo. Po zdefiniowaniu grupy można przypisać elementy <xref:System.Windows.Forms.ListView> do grup. Możesz również przenieść elementy z jednej grupy do innej programistycznie.  
  
### <a name="to-add-groups"></a>Aby dodać grupy  
  
1. Użyj metody <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> kolekcji <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Aby usunąć grupy  
  
1. Użyj metody <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> kolekcji <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     Metoda <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> usuwa pojedynczą grupę; Metoda <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> usuwa wszystkie grupy z listy.  
  
    > [!NOTE]
    > Usunięcie grupy nie powoduje usunięcia elementów należących do tej grupy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Aby przypisać elementy do grup lub przenosić elementy między grupami  
  
1. Ustaw właściwość <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> poszczególnych elementów.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView, kontrolka](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
