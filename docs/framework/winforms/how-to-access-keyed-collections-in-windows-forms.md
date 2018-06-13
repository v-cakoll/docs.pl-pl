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
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="52256-102">Porady: uzyskiwanie dostępu do kolekcji z kluczami w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="52256-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="52256-103">Można uzyskać dostępu do poszczególnych kolekcji elementów według klucza.</span><span class="sxs-lookup"><span data-stu-id="52256-103">You can access individual collection items by key.</span></span> <span data-ttu-id="52256-104">Ta funkcja dodano do wielu klas kolekcji, które są zazwyczaj używane w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="52256-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="52256-105">Poniżej przedstawiono niektóre klasy kolekcji, których dostępny kolekcje zabezpieczone kluczami:</span><span class="sxs-lookup"><span data-stu-id="52256-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="52256-106">Klucz skojarzony z elementu w kolekcji jest zazwyczaj nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="52256-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="52256-107">Poniższe procedury pokazują, jak używać klas kolekcji do wykonywania typowych zadań.</span><span class="sxs-lookup"><span data-stu-id="52256-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="52256-108">Aby znaleźć i fokus zagnieżdżony formant w kolekcji formantów</span><span class="sxs-lookup"><span data-stu-id="52256-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="52256-109">Użyj <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> i <xref:System.Windows.Forms.Control.Focus%2A> metody do określenia nazwy formantu, aby odnaleźć i nadaj fokus.</span><span class="sxs-lookup"><span data-stu-id="52256-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="52256-110">Aby uzyskać dostępu do obrazu w kolekcji obrazów</span><span class="sxs-lookup"><span data-stu-id="52256-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="52256-111">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> właściwości, aby określić nazwę obrazu, którego chcesz uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="52256-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="52256-112">Aby ustawić strony karty jako wybranej karty</span><span class="sxs-lookup"><span data-stu-id="52256-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="52256-113">Użyj <xref:System.Windows.Forms.TabControl.SelectedTab%2A> właściwości wraz z <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> właściwości, aby określić nazwę strony karty można ustawić jako wybranej karty.</span><span class="sxs-lookup"><span data-stu-id="52256-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="52256-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52256-114">See Also</span></span>  
 [<span data-ttu-id="52256-115">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52256-115">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [<span data-ttu-id="52256-116">Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52256-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
