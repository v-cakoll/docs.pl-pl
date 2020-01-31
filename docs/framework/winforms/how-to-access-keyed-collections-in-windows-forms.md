---
title: 'Instrukcje: uzyskiwanie dostępu do kolekcji z kluczami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 717ba9cc8605da08701de1bd13d6bc6da1c9b758
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739612"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Porady: uzyskiwanie dostępu do kolekcji z kluczami w formularzach systemu Windows

- Możesz uzyskać dostęp do poszczególnych elementów kolekcji według klucza. Ta funkcja została dodana do wielu klas kolekcji, które są zwykle używane przez aplikacje Windows Forms. Na poniższej liście przedstawiono niektóre klasy kolekcji, które mają dostępne kolekcje z systemem:  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klucz skojarzony z elementem w kolekcji jest zwykle nazwą elementu. W poniższych procedurach pokazano, jak używać klas kolekcji do wykonywania typowych zadań.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Aby znaleźć formant zagnieżdżony w kolekcji formantów i nadać mu fokus  
  
- Użyj metod <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> i <xref:System.Windows.Forms.Control.Focus%2A>, aby określić nazwę formantu do wyszukania i nawiązać fokus.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Aby uzyskać dostęp do obrazu w kolekcji obrazów  
  
- Użyj właściwości <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>, aby określić nazwę obrazu, do którego chcesz uzyskać dostęp.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Aby ustawić stronę karty jako wybraną kartę  
  
- Użyj właściwości <xref:System.Windows.Forms.TabControl.SelectedTab%2A> wraz z właściwością <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>, aby określić nazwę strony karty, która ma zostać ustawiona jako wybrana karta.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do formularzy Windows Forms](getting-started-with-windows-forms.md)
- [Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows Forms](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
