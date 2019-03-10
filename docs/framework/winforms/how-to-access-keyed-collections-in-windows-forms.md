---
title: 'Instrukcje: Dostęp do kolekcji z kluczami w formularzach Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: af398e8ac051bfc89c532fe5dc216e9cfbfdc4b9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709626"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="80d52-102">Instrukcje: Dostęp do kolekcji z kluczami w formularzach Windows</span><span class="sxs-lookup"><span data-stu-id="80d52-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="80d52-103">Możesz uzyskać dostęp poszczególnych kolekcji elementów według klucza.</span><span class="sxs-lookup"><span data-stu-id="80d52-103">You can access individual collection items by key.</span></span> <span data-ttu-id="80d52-104">Ta funkcja dołączonym do wielu klas kolekcji, które zazwyczaj są używane przez aplikacje Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="80d52-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="80d52-105">Na poniższej liście przedstawiono niektóre z klas kolekcji, które mają dostępne kolekcje zabezpieczone kluczami:</span><span class="sxs-lookup"><span data-stu-id="80d52-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="80d52-106">Klucz skojarzony z elementem w kolekcji jest zazwyczaj nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="80d52-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="80d52-107">Poniższe procedury pokazują, jak używać klas kolekcji do wykonywania typowych zadań.</span><span class="sxs-lookup"><span data-stu-id="80d52-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="80d52-108">Aby znaleźć i wyróżnienie zagnieżdżony formant w kolekcji formant</span><span class="sxs-lookup"><span data-stu-id="80d52-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="80d52-109">Użyj <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> i <xref:System.Windows.Forms.Control.Focus%2A> metody, aby określić nazwę formantu, aby znaleźć i nadaj fokus na.</span><span class="sxs-lookup"><span data-stu-id="80d52-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="80d52-110">Aby dostęp do obrazu w kolekcji obrazów</span><span class="sxs-lookup"><span data-stu-id="80d52-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="80d52-111">Użyj <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> właściwość, aby określić nazwę obrazu, którego chcesz uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="80d52-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="80d52-112">Aby ustawić karty jako kartę wybraną</span><span class="sxs-lookup"><span data-stu-id="80d52-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="80d52-113">Użyj <xref:System.Windows.Forms.TabControl.SelectedTab%2A> właściwości wraz z <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> właściwości, aby określić nazwę karty, aby ustawić jako kartę wybraną.</span><span class="sxs-lookup"><span data-stu-id="80d52-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="80d52-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80d52-114">See also</span></span>
- [<span data-ttu-id="80d52-115">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80d52-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="80d52-116">Instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="80d52-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
