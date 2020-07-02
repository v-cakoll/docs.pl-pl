---
title: Dodawanie i usuwanie elementów z kontrolką ListView
description: Dowiedz się, jak dodać i usunąć element z kontrolką Windows Forms ListView, określając element i przypisując do niego właściwości.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618093"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows
Proces dodawania elementu do <xref:System.Windows.Forms.ListView> kontrolki Windows Forms składa się głównie z określania elementu i przypisywania do niego właściwości. Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.  
  
### <a name="to-add-items-programmatically"></a>Aby programowo dodać elementy  
  
1. Użyj <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> metody <xref:System.Windows.Forms.ListView.Items%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Aby programowo usunąć elementy  
  
1. Użyj <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> metody lub <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> <xref:System.Windows.Forms.ListView.Items%2A> właściwości. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>Metoda usuwa pojedynczy element; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> Metoda usuwa wszystkie elementy z listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [ListView — Formant](listview-control-windows-forms.md)
- [ListView — Informacje o formancie](listview-control-overview-windows-forms.md)
