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
ms.openlocfilehash: fdd3a56ab9a267990bb0e832c0d4cc2af9334034
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214043"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Instrukcje: Uzyskiwanie dostępu do kolekcji z kluczami w formularzach Windows Forms
-   Możesz uzyskać dostęp poszczególnych kolekcji elementów według klucza. Ta funkcja dołączonym do wielu klas kolekcji, które zazwyczaj są używane przez aplikacje Windows Forms. Na poniższej liście przedstawiono niektóre z klas kolekcji, które mają dostępne kolekcje zabezpieczone kluczami:  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klucz skojarzony z elementem w kolekcji jest zazwyczaj nazwa elementu. Poniższe procedury pokazują, jak używać klas kolekcji do wykonywania typowych zadań.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Aby znaleźć i wyróżnienie zagnieżdżony formant w kolekcji formant  
  
-   Użyj <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> i <xref:System.Windows.Forms.Control.Focus%2A> metody, aby określić nazwę formantu, aby znaleźć i nadaj fokus na.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Aby dostęp do obrazu w kolekcji obrazów  
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> właściwość, aby określić nazwę obrazu, którego chcesz uzyskać dostęp.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Aby ustawić karty jako kartę wybraną  
  
-   Użyj <xref:System.Windows.Forms.TabControl.SelectedTab%2A> właściwości wraz z <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> właściwości, aby określić nazwę karty, aby ustawić jako kartę wybraną.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do formularzy systemu Windows](getting-started-with-windows-forms.md)
- [Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy systemu Windows](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
