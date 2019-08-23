---
title: 'Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966632"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows
Za pomocą funkcji <xref:System.Windows.Forms.ListView> grupowania formantu można wyświetlić powiązane zestawy elementów w grupach. Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup. <xref:System.Windows.Forms.ListView> Grupy umożliwiają łatwiejsze nawigowanie po dużych listach, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne. Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy.  
  
 ![Zrzut ekranu przedstawiający nieparzystą i parzystą grupę ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w projektancie lub programowo. Po zdefiniowaniu grupy można przypisać <xref:System.Windows.Forms.ListView> elementy do grup. Możesz również przenieść elementy z jednej grupy do innej programistycznie.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ListView>grupy są dostępne tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> gdy aplikacja wywołuje metodę. We wcześniejszych systemach operacyjnych każdy kod dotyczący grup nie ma wpływu, a grupy nie będą wyświetlane. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Aby dodać grupy  
  
1. <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> Użyj metody<xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Aby usunąć grupy  
  
1. <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> Użyj metody <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub<xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.  
  
     Metoda usuwa pojedynczą grupę <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ; Metoda usuwa wszystkie grupy z listy. <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>  
  
    > [!NOTE]
    > Usunięcie grupy nie powoduje usunięcia elementów należących do tej grupy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Aby przypisać elementy do grup lub przenosić elementy między grupami  
  
1. <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> Ustaw właściwość poszczególnych elementów.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
