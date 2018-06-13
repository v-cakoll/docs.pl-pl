---
title: 'Porady: zaznaczanie elementu w formancie ListView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 8256eaeddf98c5a0dd80357bcd562e8f66db85b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532824"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="b6668-102">Porady: zaznaczanie elementu w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b6668-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="b6668-103">W tym przykładzie pokazano, jak programowo wybierz element w formularzach systemu Windows <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="b6668-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b6668-104">Programowy Wybór elementu nie zmienia się automatycznie fokusu <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="b6668-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b6668-105">Z tego powodu będzie zwykle również chcesz ustawić element zgodnie z fokusem, gdy zaznaczenie elementu.</span><span class="sxs-lookup"><span data-stu-id="b6668-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6668-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6668-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6668-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b6668-107">Compiling the Code</span></span>  
 <span data-ttu-id="b6668-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b6668-108">This example requires:</span></span>  
  
-   <span data-ttu-id="b6668-109">A <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` zawiera co najmniej jeden element.</span><span class="sxs-lookup"><span data-stu-id="b6668-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="b6668-110">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b6668-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6668-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6668-111">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
