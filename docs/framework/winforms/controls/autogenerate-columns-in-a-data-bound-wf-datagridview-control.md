---
title: Automatyczne generowanie kolumn w formancie DataGridView powiązanym z danymi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 860e640e095537358d2f8778c810aa577e9d7ff0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746233"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="94684-102">Porady: automatyczne generowanie kolumn w powiązanym z danymi formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94684-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="94684-103">Poniższy przykład kodu demonstruje sposób wyświetlania kolumn z powiązanego źródła danych w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="94684-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="94684-104">Gdy <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> wartość właściwości jest `true` (domyślnie), <xref:System.Windows.Forms.DataGridViewColumn> jest tworzony dla każdej kolumny w tabeli źródła danych.</span><span class="sxs-lookup"><span data-stu-id="94684-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="94684-105">Jeśli kontrolka <xref:System.Windows.Forms.DataGridView> ma już kolumny podczas ustawiania właściwości <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, istniejące powiązane kolumny są porównywane z kolumnami w źródle danych i zachowywane za każdym razem, gdy istnieje dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="94684-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="94684-106">Kolumny niepowiązane są zawsze zachowywane.</span><span class="sxs-lookup"><span data-stu-id="94684-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="94684-107">Powiązane kolumny, dla których nie ma dopasowania w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="94684-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="94684-108">Kolumny w źródle danych, dla których nie ma dopasowania w formancie, generują nowe <xref:System.Windows.Forms.DataGridViewColumn> obiekty, które są dodawane na końcu kolekcji <xref:System.Windows.Forms.DataGridView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="94684-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94684-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="94684-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94684-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="94684-110">Compiling the Code</span></span>  
 <span data-ttu-id="94684-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="94684-111">This example requires:</span></span>  
  
- <span data-ttu-id="94684-112">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="94684-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
- <span data-ttu-id="94684-113">Obiekt <xref:System.Data.DataSet> o nazwie `customersDataSet`, który ma tabelę o nazwie `Customers`.</span><span class="sxs-lookup"><span data-stu-id="94684-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
- <span data-ttu-id="94684-114">Odwołania do zestawów <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>i <xref:System.Xml?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="94684-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94684-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94684-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="94684-116">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94684-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="94684-117">Instrukcje: usuwanie utworzonych automatycznie kolumn z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94684-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
