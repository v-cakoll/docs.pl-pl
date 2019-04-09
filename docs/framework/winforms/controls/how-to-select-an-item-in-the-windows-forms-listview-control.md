---
title: 'Instrukcje: zaznaczanie elementu w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: b3cfcc6c2873dfb0eb95cf7950adc6b2bb73e74c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143185"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="aee2d-102">Instrukcje: zaznaczanie elementu w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="aee2d-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="aee2d-103">W tym przykładzie pokazano, jak programowo wybierz element w formularzach Windows <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="aee2d-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="aee2d-104">Zaznaczenie elementu programowo nie zmieni automatycznie fokus na <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="aee2d-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="aee2d-105">Z tego powodu zwykle także można ustawić elementu, ponieważ skupia się po wybraniu elementu.</span><span class="sxs-lookup"><span data-stu-id="aee2d-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aee2d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="aee2d-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aee2d-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="aee2d-107">Compiling the Code</span></span>  
 <span data-ttu-id="aee2d-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="aee2d-108">This example requires:</span></span>  
  
-   <span data-ttu-id="aee2d-109">A <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` zawierający co najmniej jeden element.</span><span class="sxs-lookup"><span data-stu-id="aee2d-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="aee2d-110">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="aee2d-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee2d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aee2d-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
