---
title: 'Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: cb3a826262a49a8653e3a344bd126d434f2522dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073062"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bffaa-102">Instrukcje: użycie szablonu wiersza do dostosowania wierszy w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bffaa-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bffaa-103"><xref:System.Windows.Forms.DataGridView> Kontroli używa szablonu wiersza jako podstawy dla wszystkich wierszy, które są dodawane do formantu za pomocą powiązania danych lub po wywołaniu <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody bez określania istniejącego wiersza do użycia.</span><span class="sxs-lookup"><span data-stu-id="bffaa-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="bffaa-104">Szablon wiersza zapewnia większą kontrolę nad wyglądem i zachowaniem wierszy niż <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> zawiera właściwość.</span><span class="sxs-lookup"><span data-stu-id="bffaa-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="bffaa-105">Za pomocą szablonu wiersza można ustawić dowolny <xref:System.Windows.Forms.DataGridViewRow> właściwości, w tym <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="bffaa-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="bffaa-106">Istnieją sytuacje, w którym musi użycie szablonu wiersza do osiągnięcia określonej efekt.</span><span class="sxs-lookup"><span data-stu-id="bffaa-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="bffaa-107">Na przykład, nie mogą być przechowywane informacje o wysokości wiersza <xref:System.Windows.Forms.DataGridViewCellStyle>, więc musisz można zmienić wysokość domyślna używana przez wszystkie wiersze, używając szablonu wiersza.</span><span class="sxs-lookup"><span data-stu-id="bffaa-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="bffaa-108">Szablon wiersza jest przydatna podczas tworzenia własnych klas pochodnych <xref:System.Windows.Forms.DataGridViewRow> i chcesz, aby używany, gdy nowe wiersze są dodawane do formantu niestandardowego typu.</span><span class="sxs-lookup"><span data-stu-id="bffaa-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bffaa-109">Szablon wiersza jest używana tylko wtedy, gdy zostaną dodane wiersze.</span><span class="sxs-lookup"><span data-stu-id="bffaa-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="bffaa-110">Nie można zmienić istniejące wiersze, zmieniając szablonu wiersza.</span><span class="sxs-lookup"><span data-stu-id="bffaa-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="bffaa-111">Użycie szablonu wiersza</span><span class="sxs-lookup"><span data-stu-id="bffaa-111">To use the row template</span></span>  
  
-   <span data-ttu-id="bffaa-112">Ustawianie właściwości w obiekcie pobierane <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bffaa-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bffaa-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bffaa-113">Compiling the Code</span></span>  
 <span data-ttu-id="bffaa-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="bffaa-114">This example requires:</span></span>  
  
-   <span data-ttu-id="bffaa-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="bffaa-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="bffaa-116">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="bffaa-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffaa-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bffaa-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bffaa-118">Podstawowe formatowanie i style w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bffaa-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bffaa-119">Style komórki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bffaa-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
