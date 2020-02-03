---
title: Zapobiegaj dodawaniu i usuwaniu wierszy w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728722"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5615c-102">Porady: zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5615c-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5615c-103">Czasami chcesz uniemożliwić użytkownikom wprowadzanie nowych wierszy danych lub usuwanie istniejących wierszy w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5615c-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5615c-104">Właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> wskazuje, czy wiersz dla nowych rekordów znajduje się u dołu kontrolki, natomiast Właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> wskazuje, czy można usunąć wiersze.</span><span class="sxs-lookup"><span data-stu-id="5615c-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="5615c-105">Poniższy przykład kodu używa tych właściwości, a także ustawia właściwość <xref:System.Windows.Forms.DataGridView.ReadOnly%2A>, aby kontrolka była całkowicie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5615c-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="5615c-106">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5615c-106">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="5615c-107">Zobacz również [instrukcje: Zapobieganie dodawaniu i usuwaniu wierszy w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="5615c-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5615c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5615c-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5615c-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5615c-109">Compiling the Code</span></span>  
 <span data-ttu-id="5615c-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5615c-110">This example requires:</span></span>  
  
- <span data-ttu-id="5615c-111">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="5615c-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="5615c-112">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5615c-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5615c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5615c-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5615c-114">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5615c-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
