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
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="5757b-102">Instrukcje: Uzyskiwanie dostępu do kolekcji z kluczami w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5757b-102">How to: Access Keyed Collections in Windows Forms</span></span>

- <span data-ttu-id="5757b-103">Możesz uzyskać dostęp do poszczególnych elementów kolekcji według klucza.</span><span class="sxs-lookup"><span data-stu-id="5757b-103">You can access individual collection items by key.</span></span> <span data-ttu-id="5757b-104">Ta funkcja została dodana do wielu klas kolekcji, które są zwykle używane przez aplikacje Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5757b-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="5757b-105">Na poniższej liście przedstawiono niektóre klasy kolekcji, które mają dostępne kolekcje z systemem:</span><span class="sxs-lookup"><span data-stu-id="5757b-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="5757b-106">Klucz skojarzony z elementem w kolekcji jest zwykle nazwą elementu.</span><span class="sxs-lookup"><span data-stu-id="5757b-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="5757b-107">W poniższych procedurach pokazano, jak używać klas kolekcji do wykonywania typowych zadań.</span><span class="sxs-lookup"><span data-stu-id="5757b-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="5757b-108">Aby znaleźć formant zagnieżdżony w kolekcji formantów i nadać mu fokus</span><span class="sxs-lookup"><span data-stu-id="5757b-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="5757b-109">Użyj metod <xref:System.Windows.Forms.Control.Focus%2A> i, aby określić nazwę formantu do wyszukania i nadawać fokus. <xref:System.Windows.Forms.Control.ControlCollection.Find%2A></span><span class="sxs-lookup"><span data-stu-id="5757b-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="5757b-110">Aby uzyskać dostęp do obrazu w kolekcji obrazów</span><span class="sxs-lookup"><span data-stu-id="5757b-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="5757b-111">Użyj właściwości <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> , aby określić nazwę obrazu, do którego chcesz uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="5757b-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="5757b-112">Aby ustawić stronę karty jako wybraną kartę</span><span class="sxs-lookup"><span data-stu-id="5757b-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="5757b-113">Użyj właściwości wraz <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> z właściwością, aby określić nazwę strony karty, która ma zostać ustawiona jako wybrana karta. <xref:System.Windows.Forms.TabControl.SelectedTab%2A></span><span class="sxs-lookup"><span data-stu-id="5757b-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5757b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5757b-114">See also</span></span>

- [<span data-ttu-id="5757b-115">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5757b-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="5757b-116">Instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList</span><span class="sxs-lookup"><span data-stu-id="5757b-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
