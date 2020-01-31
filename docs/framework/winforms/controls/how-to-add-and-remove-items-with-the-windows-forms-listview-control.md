---
title: Dodawanie i usuwanie elementów z kontrolką ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743139"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows
Proces dodawania elementu do kontrolki <xref:System.Windows.Forms.ListView> Windows Forms składa się głównie z określania elementu i przypisywania do niego właściwości. Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.  
  
### <a name="to-add-items-programmatically"></a>Aby programowo dodać elementy  
  
1. Użyj metody <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> właściwości <xref:System.Windows.Forms.ListView.Items%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Aby programowo usunąć elementy  
  
1. Użyj metody <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> lub <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> właściwości <xref:System.Windows.Forms.ListView.Items%2A>. Metoda <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> usuwa pojedynczy element; Metoda <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> usuwa wszystkie elementy z listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [ListView, kontrolka](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
