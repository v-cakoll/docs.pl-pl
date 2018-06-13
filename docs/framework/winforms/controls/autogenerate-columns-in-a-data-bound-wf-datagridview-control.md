---
title: 'Porady: automatyczne generowanie kolumn w powiązanym z danymi formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 97fbc2c21f618b9fa0451c17ebf87579f51a3f0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524390"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="32a7b-102">Porady: automatyczne generowanie kolumn w powiązanym z danymi formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="32a7b-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="32a7b-103">Poniższy przykład kodu pokazuje sposób wyświetlania kolumn ze źródła danych powiązania w <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="32a7b-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="32a7b-104">Gdy <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> wartość właściwości jest `true` (ustawienie domyślne), <xref:System.Windows.Forms.DataGridViewColumn> jest tworzona dla każdej kolumny w tabeli źródła danych.</span><span class="sxs-lookup"><span data-stu-id="32a7b-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="32a7b-105">Jeśli <xref:System.Windows.Forms.DataGridView> formantu ma już kolumny po ustawieniu <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> właściwości, granica istniejące kolumny są w porównaniu do kolumn w źródle danych i zachowane zawsze, gdy są zgodne.</span><span class="sxs-lookup"><span data-stu-id="32a7b-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="32a7b-106">Niepowiązanych kolumn zawsze są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="32a7b-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="32a7b-107">Powiązane kolumny, dla których nie zostanie odnaleziony odpowiednik w źródle danych są usuwane.</span><span class="sxs-lookup"><span data-stu-id="32a7b-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="32a7b-108">Kolumny w źródle danych, dla którego nie zostanie odnaleziony odpowiednik w formancie Generuj nowy <xref:System.Windows.Forms.DataGridViewColumn> obiektów, które są dodawane na końcu <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="32a7b-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32a7b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="32a7b-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32a7b-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="32a7b-110">Compiling the Code</span></span>  
 <span data-ttu-id="32a7b-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="32a7b-111">This example requires:</span></span>  
  
-   <span data-ttu-id="32a7b-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="32a7b-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
-   <span data-ttu-id="32a7b-113">A <xref:System.Data.DataSet> obiektu o nazwie `customersDataSet` mający tabela o nazwie `Customers`.</span><span class="sxs-lookup"><span data-stu-id="32a7b-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
-   <span data-ttu-id="32a7b-114">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, i <xref:System.Xml?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="32a7b-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a7b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32a7b-115">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="32a7b-116">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32a7b-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="32a7b-117">Instrukcje: usuwanie utworzonych automatycznie kolumn z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32a7b-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)
