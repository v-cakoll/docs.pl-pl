---
title: Ukryj kolumny w formancie DataGridView
description: Dowiedz się, jak programowo ukryć kolumny w kontrolce DataGridView Windows Forms, ustawiając właściwość DataGridViewColumn. Visible na wartość false.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 27e9f331151acd68d76233bc7dbb09c2d870afde
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618054"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="98fb1-103">Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="98fb1-103">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="98fb1-104">Czasami chcesz wyświetlić tylko niektóre kolumny, które są dostępne w <xref:System.Windows.Forms.DataGridView> kontrolce Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="98fb1-104">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98fb1-105">Na przykład możesz chcieć wyświetlić kolumnę wynagrodzenia pracownika dla użytkowników z poświadczeniami zarządzania, jednocześnie ukrywając ją od innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="98fb1-105">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="98fb1-106">Alternatywnie możesz chcieć powiązać formant ze źródłem danych zawierającym wiele kolumn, tylko niektóre, które chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="98fb1-106">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="98fb1-107">W takim przypadku zwykle usuniesz kolumny, które nie są wyświetlane, zamiast ich ukrywania.</span><span class="sxs-lookup"><span data-stu-id="98fb1-107">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="98fb1-108">W <xref:System.Windows.Forms.DataGridView> kontrolce <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> wartość właściwości kolumny określa, czy ta kolumna jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="98fb1-108">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="98fb1-109">To zadanie jest obsługiwane w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98fb1-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="98fb1-110">Zobacz również [instrukcje: Ukrywanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="98fb1-110">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="98fb1-111">Aby programowo ukryć kolumnę</span><span class="sxs-lookup"><span data-stu-id="98fb1-111">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="98fb1-112">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> Właściwość na wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="98fb1-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="98fb1-113">Aby ukryć `CustomerID` kolumnę, która jest generowana automatycznie podczas tworzenia powiązania danych, umieść w <xref:System.Windows.Forms.DataGridView.DataBindingComplete> obsłudze zdarzeń Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="98fb1-113">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98fb1-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="98fb1-114">Compiling the Code</span></span>  
 <span data-ttu-id="98fb1-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="98fb1-115">This example requires:</span></span>  
  
- <span data-ttu-id="98fb1-116"><xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie `dataGridView1` , która zawiera kolumnę o nazwie `CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="98fb1-116">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="98fb1-117">Odwołania do <xref:System?displayProperty=nameWithType> zestawów i <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="98fb1-117">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fb1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98fb1-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="98fb1-119">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98fb1-119">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="98fb1-120">Porady: usuwanie utworzonych automatycznie kolumn z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="98fb1-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="98fb1-121">Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98fb1-121">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
