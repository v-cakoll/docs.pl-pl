---
title: 'Porady: uzyskiwanie dostępu do kolekcji z kluczami w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 59e5cea29ee520b1f13f8fae98ae4042cc86fef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538731"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Porady: uzyskiwanie dostępu do kolekcji z kluczami w formularzach systemu Windows
-   Można uzyskać dostępu do poszczególnych kolekcji elementów według klucza. Ta funkcja dodano do wielu klas kolekcji, które są zazwyczaj używane w formularzach systemu Windows. Poniżej przedstawiono niektóre klasy kolekcji, których dostępny kolekcje zabezpieczone kluczami:  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klucz skojarzony z elementu w kolekcji jest zazwyczaj nazwa elementu. Poniższe procedury pokazują, jak używać klas kolekcji do wykonywania typowych zadań.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Aby znaleźć i fokus zagnieżdżony formant w kolekcji formantów  
  
-   Użyj <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> i <xref:System.Windows.Forms.Control.Focus%2A> metody do określenia nazwy formantu, aby odnaleźć i nadaj fokus.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Aby uzyskać dostępu do obrazu w kolekcji obrazów  
  
-   Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> właściwości, aby określić nazwę obrazu, którego chcesz uzyskać dostęp.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Aby ustawić strony karty jako wybranej karty  
  
-   Użyj <xref:System.Windows.Forms.TabControl.SelectedTab%2A> właściwości wraz z <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> właściwości, aby określić nazwę strony karty można ustawić jako wybranej karty.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do formularzy Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows Forms](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
