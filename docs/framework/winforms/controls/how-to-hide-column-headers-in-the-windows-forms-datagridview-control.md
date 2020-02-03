---
title: Ukryj nagłówki kolumn w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: d84c93b0ad1c9ef456c73dd29af1de4857778999
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736585"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="35122-102">Porady: ukrywanie nagłówków kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35122-102">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="35122-103">Czasami chcesz wyświetlić <xref:System.Windows.Forms.DataGridView> bez nagłówków kolumn.</span><span class="sxs-lookup"><span data-stu-id="35122-103">Sometimes you will want to display a <xref:System.Windows.Forms.DataGridView> without column headers.</span></span> <span data-ttu-id="35122-104">W kontrolce <xref:System.Windows.Forms.DataGridView> wartość właściwości <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> określa, czy nagłówki kolumn są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="35122-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> property value determines whether the column headers are displayed.</span></span>  
  
### <a name="to-hide-the-column-headers"></a><span data-ttu-id="35122-105">Aby ukryć nagłówki kolumn</span><span class="sxs-lookup"><span data-stu-id="35122-105">To hide the column headers</span></span>  
  
- <span data-ttu-id="35122-106">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="35122-106">Set the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35122-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35122-107">Compiling the Code</span></span>  
 <span data-ttu-id="35122-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="35122-108">This example requires:</span></span>  
  
- <span data-ttu-id="35122-109">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="35122-109">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="35122-110">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35122-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35122-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35122-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="35122-112">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35122-112">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
