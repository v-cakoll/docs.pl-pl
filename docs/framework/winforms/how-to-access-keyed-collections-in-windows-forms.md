---
title: 'Instrukcje: Uzyskiwanie dostępu do kolekcji z kluczami w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: a88e4766a1e774582bcd0356c9b6e77bc31f1960
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928523"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Instrukcje: Uzyskiwanie dostępu do kolekcji z kluczami w formularzach Windows Forms

- Możesz uzyskać dostęp do poszczególnych elementów kolekcji według klucza. Ta funkcja została dodana do wielu klas kolekcji, które są zwykle używane przez aplikacje Windows Forms. Na poniższej liście przedstawiono niektóre klasy kolekcji, które mają dostępne kolekcje z systemem:  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klucz skojarzony z elementem w kolekcji jest zwykle nazwą elementu. W poniższych procedurach pokazano, jak używać klas kolekcji do wykonywania typowych zadań.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Aby znaleźć formant zagnieżdżony w kolekcji formantów i nadać mu fokus  
  
- Użyj metod <xref:System.Windows.Forms.Control.Focus%2A> i, aby określić nazwę formantu do wyszukania i nadawać fokus. <xref:System.Windows.Forms.Control.ControlCollection.Find%2A>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Aby uzyskać dostęp do obrazu w kolekcji obrazów  
  
- Użyj właściwości <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> , aby określić nazwę obrazu, do którego chcesz uzyskać dostęp.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Aby ustawić stronę karty jako wybraną kartę  
  
- Użyj właściwości wraz <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> z właściwością, aby określić nazwę strony karty, która ma zostać ustawiona jako wybrana karta. <xref:System.Windows.Forms.TabControl.SelectedTab%2A>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do formularzy Windows Forms](getting-started-with-windows-forms.md)
- [Instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
