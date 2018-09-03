---
title: 'Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 2ddf4b0701ea563465ca3023c73f588f4e0f3a5f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488043"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4deaa-102">Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4deaa-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4deaa-103">Czasami warto wyświetlić tylko niektóre kolumny, które są dostępne w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="4deaa-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="4deaa-104">Na przykład możesz chcieć wyświetlić pracownika wynagrodzenia kolumny do użytkowników przy użyciu poświadczeń zarządzania podczas ukrywając je od innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4deaa-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="4deaa-105">Alternatywnie można powiązać formant ze źródłem danych, który zawiera wiele kolumn, tylko niektóre z nich, którą chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="4deaa-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="4deaa-106">W tym przypadku zazwyczaj spowoduje usunięcie kolumn, użytkownik nie jest w trakcie wyświetlania, a nie je ukryć.</span><span class="sxs-lookup"><span data-stu-id="4deaa-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="4deaa-107">W <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> wartość właściwości kolumny określa, czy ta kolumna jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="4deaa-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="4deaa-108">Są obsługiwane dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4deaa-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="4deaa-109">Zobacz też [porady: ukrywanie kolumn w Windows Forms DataGridView kontroli przy użyciu narzędzia Projektant](https://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="4deaa-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="4deaa-110">Aby ukryć kolumnę programowe</span><span class="sxs-lookup"><span data-stu-id="4deaa-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="4deaa-111">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="4deaa-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="4deaa-112">Aby ukryć `CustomerID` kolumny, która jest generowana automatycznie podczas tworzenia powiązań danych, umieść poniższy przykład kodu w <xref:System.Windows.Forms.DataGridView.DataBindingComplete> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4deaa-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4deaa-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4deaa-113">Compiling the Code</span></span>  
 <span data-ttu-id="4deaa-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4deaa-114">This example requires:</span></span>  
  
-   <span data-ttu-id="4deaa-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawierającą kolumnę o nazwie `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="4deaa-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="4deaa-116">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="4deaa-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4deaa-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4deaa-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4deaa-118">Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4deaa-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="4deaa-119">Instrukcje: usuwanie utworzonych automatycznie kolumn z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4deaa-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="4deaa-120">Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4deaa-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
