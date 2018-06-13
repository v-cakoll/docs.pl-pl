---
title: 'Porady: zmienianie stylów obramowania i linii siatki w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 94e5ae11d7fb2b67e028f368183246f8d8543a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528752"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="80b55-102">Porady: zmienianie stylów obramowania i linii siatki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80b55-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="80b55-103">Z <xref:System.Windows.Forms.DataGridView> sterowania, można dostosować wygląd obramowania i linii siatki, aby ulepszyć środowisko użytkownika formantu.</span><span class="sxs-lookup"><span data-stu-id="80b55-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="80b55-104">Można zmodyfikować kolor linii siatki i styl obramowania formantu oprócz style obramowania komórek w formancie.</span><span class="sxs-lookup"><span data-stu-id="80b55-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="80b55-105">Można także zastosować dla innej komórki Style obramowania komórek zwykłej, komórek nagłówka wiersza i komórki nagłówka kolumny.</span><span class="sxs-lookup"><span data-stu-id="80b55-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80b55-106">Kolor linii siatki jest używana tylko z <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, i <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> wartości <xref:System.Windows.Forms.DataGridViewCellBorderStyle> wyliczenie i <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> wartość <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="80b55-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="80b55-107">Wartości te wyliczenia Użyj kolorów określonego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="80b55-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="80b55-108">Ponadto, jeżeli style wizualne są włączone w systemach Windows XP i rodziny Windows Server 2003 za pośrednictwem <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.DataGridView.GridColor%2A> nie jest używana wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="80b55-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="80b55-109">Aby programowo zmienić kolor linii siatki</span><span class="sxs-lookup"><span data-stu-id="80b55-109">To change the gridline color programmatically</span></span>  
  
-   <span data-ttu-id="80b55-110">Ustaw <xref:System.Windows.Forms.DataGridView.GridColor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="80b55-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="80b55-111">Aby programowo zmienić styl obramowania formantu DataGridView całego</span><span class="sxs-lookup"><span data-stu-id="80b55-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
-   <span data-ttu-id="80b55-112">Ustaw <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> jedną z właściwości <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="80b55-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="80b55-113">Aby programowo zmienić style obramowania komórek DataGridView</span><span class="sxs-lookup"><span data-stu-id="80b55-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
-   <span data-ttu-id="80b55-114">Ustaw <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, i <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="80b55-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="80b55-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="80b55-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80b55-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80b55-116">Compiling the Code</span></span>  
 <span data-ttu-id="80b55-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="80b55-117">This example requires:</span></span>  
  
-   <span data-ttu-id="80b55-118">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="80b55-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="80b55-119">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Drawing?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="80b55-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b55-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80b55-120">See Also</span></span>  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [<span data-ttu-id="80b55-121">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80b55-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
