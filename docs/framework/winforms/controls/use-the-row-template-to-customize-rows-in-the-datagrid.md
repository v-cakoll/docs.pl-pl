---
title: Użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728386"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="238f6-102">Porady: użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="238f6-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="238f6-103">Formant <xref:System.Windows.Forms.DataGridView> używa szablonu wiersza jako podstawy dla wszystkich wierszy, które dodaje do formantu za pośrednictwem powiązania danych lub wywołania metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> bez określania istniejącego wiersza do użycia.</span><span class="sxs-lookup"><span data-stu-id="238f6-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="238f6-104">Szablon wiersza zapewnia większą kontrolę nad wyglądem i zachowaniem wierszy, niż zapewnia Właściwość <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="238f6-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="238f6-105">Za pomocą szablonu wiersza można ustawić wszystkie <xref:System.Windows.Forms.DataGridViewRow> właściwości, w tym <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="238f6-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="238f6-106">Istnieją sytuacje, w których należy użyć szablonu wiersza do osiągnięcia określonego efektu.</span><span class="sxs-lookup"><span data-stu-id="238f6-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="238f6-107">Na przykład informacje o wysokości wiersza nie mogą być przechowywane w <xref:System.Windows.Forms.DataGridViewCellStyle>, więc musisz użyć szablonu wiersza, aby zmienić domyślną wysokość używaną przez wszystkie wiersze.</span><span class="sxs-lookup"><span data-stu-id="238f6-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="238f6-108">Szablon wiersza jest również przydatny podczas tworzenia własnych klas pochodnych z <xref:System.Windows.Forms.DataGridViewRow> i chcesz, aby typ niestandardowy był używany podczas dodawania nowych wierszy do formantu.</span><span class="sxs-lookup"><span data-stu-id="238f6-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="238f6-109">Szablon wiersza jest używany tylko po dodaniu wierszy.</span><span class="sxs-lookup"><span data-stu-id="238f6-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="238f6-110">Nie można zmienić istniejących wierszy, zmieniając szablon wiersza.</span><span class="sxs-lookup"><span data-stu-id="238f6-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="238f6-111">Aby użyć szablonu wiersza</span><span class="sxs-lookup"><span data-stu-id="238f6-111">To use the row template</span></span>  
  
- <span data-ttu-id="238f6-112">Ustaw właściwości obiektu pobranego z właściwości <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="238f6-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="238f6-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="238f6-113">Compiling the Code</span></span>  
 <span data-ttu-id="238f6-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="238f6-114">This example requires:</span></span>  
  
- <span data-ttu-id="238f6-115">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="238f6-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="238f6-116">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="238f6-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238f6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="238f6-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="238f6-118">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="238f6-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="238f6-119">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="238f6-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
