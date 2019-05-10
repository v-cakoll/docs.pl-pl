---
title: 'Instrukcje: automatyczne generowanie kolumn w powiązaną z danymi kontrolką DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: eb74c1ef1661fc8bd7a57f079f10d24a7eef8187
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639767"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="dffed-102">Instrukcje: automatyczne generowanie kolumn w powiązaną z danymi kontrolką DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dffed-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="dffed-103">Poniższy przykład kodu demonstruje sposób wyświetlania kolumn ze źródła danych powiązanych w <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="dffed-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="dffed-104">Gdy <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> wartość właściwości jest `true` (ustawienie domyślne), <xref:System.Windows.Forms.DataGridViewColumn> jest tworzony dla każdej kolumny w tabeli źródła danych.</span><span class="sxs-lookup"><span data-stu-id="dffed-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="dffed-105">Jeśli <xref:System.Windows.Forms.DataGridView> kontroli ma już kolumny po ustawieniu <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> właściwość, istniejące powiązane z kolumny są w porównaniu do kolumn w źródle danych i zachowane w każdym przypadku, gdy są zgodne.</span><span class="sxs-lookup"><span data-stu-id="dffed-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="dffed-106">Niepowiązanych kolumn są zawsze zachowywane.</span><span class="sxs-lookup"><span data-stu-id="dffed-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="dffed-107">Powiązane kolumny, dla których nie ma dopasowania w źródle danych są usuwane.</span><span class="sxs-lookup"><span data-stu-id="dffed-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="dffed-108">Kolumny w źródle danych, dla którego nie ma dopasowania w kontrolce Generuj nowy <xref:System.Windows.Forms.DataGridViewColumn> obiektów, które są dodawane na końcu <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dffed-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dffed-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="dffed-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dffed-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="dffed-110">Compiling the Code</span></span>  
 <span data-ttu-id="dffed-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="dffed-111">This example requires:</span></span>  
  
- <span data-ttu-id="dffed-112">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="dffed-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
- <span data-ttu-id="dffed-113">A <xref:System.Data.DataSet> obiektu o nazwie `customersDataSet` zawierającej tabelę o nazwie `Customers`.</span><span class="sxs-lookup"><span data-stu-id="dffed-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
- <span data-ttu-id="dffed-114">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, i <xref:System.Xml?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="dffed-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffed-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dffed-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dffed-116">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dffed-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="dffed-117">Instrukcje: Usuwanie utworzonych automatycznie kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dffed-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
