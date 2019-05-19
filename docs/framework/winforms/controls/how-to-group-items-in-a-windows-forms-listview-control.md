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
ms.openlocfilehash: bbca1d76f747f53103095c916605ce7335207f51
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882376"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows
Z funkcji grupowania <xref:System.Windows.Forms.ListView> kontrolki, można wyświetlić powiązane zestawy elementów w grupach. Te grupy są oddzielone na ekranie nagłówków grup poziomej, zawierające tytułów grup. Możesz użyć <xref:System.Windows.Forms.ListView> grup, aby upewnić się, przechodząc duże listy łatwiejsze przez grupowanie elementów w kolejności alfabetycznej, według daty lub przez inne logiczne grupowanie. Na poniższej ilustracji przedstawiono niektóre zgrupowanych elementów.  
  
 ![Zrzut ekranu przedstawiający nieparzysta, a nawet grupy ListView.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jedną grupę w Projektancie lub programowo. Po zdefiniowaniu grupy można przypisać <xref:System.Windows.Forms.ListView> elementów do grupy. To może również przenieść elementy z jednej grupy do innego programowo.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> grupy są dostępne tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych jakiegokolwiek kodu dotyczące grup nie ma wpływu, a grupy nie będą widoczne. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Aby dodać grupy  
  
1. Użyj <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Aby usunąć grupy  
  
1. Użyj <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metody <xref:System.Windows.Forms.ListView.Groups%2A> kolekcji.  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Metoda usuwa pojedynczą grupę; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> metoda usuwa wszystkie grupy z listy.  
  
    > [!NOTE]
    >  Usunięcie grupy nie powoduje usunięcia elementów zawartych w tej grupie.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Przypisywanie elementów do grupy lub przenosić elementy między grupami  
  
1. Ustaw <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> właściwości poszczególnych elementów.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
