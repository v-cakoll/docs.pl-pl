---
title: Sortuj i Filtruj dane ADO.NET za pomocą składnika BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742975"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="61ad5-102">Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="61ad5-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="61ad5-103">Można uwidocznić możliwości sortowania i filtrowania <xref:System.Windows.Forms.BindingSource> kontroli za pomocą właściwości <xref:System.Windows.Forms.BindingSource.Sort%2A> i <xref:System.Windows.Forms.BindingSource.Filter%2A>.</span><span class="sxs-lookup"><span data-stu-id="61ad5-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="61ad5-104">Można zastosować proste sortowanie, gdy bazowe źródło danych jest <xref:System.ComponentModel.IBindingList>i można zastosować filtrowanie i zaawansowane sortowanie, gdy źródło danych jest <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="61ad5-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="61ad5-105">Właściwość <xref:System.Windows.Forms.BindingSource.Sort%2A> wymaga standardowej składni ADO.NET: ciąg reprezentujący nazwę kolumny danych w źródle danych, po której następuje `ASC` lub `DESC`, aby wskazać, czy lista powinna być posortowana w kolejności rosnącej czy malejącej.</span><span class="sxs-lookup"><span data-stu-id="61ad5-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="61ad5-106">Można ustawić zaawansowane sortowanie lub sortowanie z wieloma kolumnami, oddzielając poszczególne kolumny średnikami.</span><span class="sxs-lookup"><span data-stu-id="61ad5-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="61ad5-107">Właściwość <xref:System.Windows.Forms.BindingSource.Filter%2A> przyjmuje wyrażenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="61ad5-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61ad5-108">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="61ad5-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="61ad5-109">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="61ad5-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="61ad5-110">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="61ad5-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="61ad5-111">Aby odfiltrować dane za pomocą parametru BindingSource</span><span class="sxs-lookup"><span data-stu-id="61ad5-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="61ad5-112">Ustaw właściwość <xref:System.Windows.Forms.BindingSource.Filter%2A> na wyrażenie, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="61ad5-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="61ad5-113">W poniższym przykładzie kodu wyrażenie jest nazwą kolumny, a następnie wartością, która ma być dla kolumny.</span><span class="sxs-lookup"><span data-stu-id="61ad5-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="61ad5-114">Aby posortować dane za pomocą parametru BindingSource</span><span class="sxs-lookup"><span data-stu-id="61ad5-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="61ad5-115">Ustaw właściwość <xref:System.Windows.Forms.BindingSource.Sort%2A> na nazwę kolumny, która ma następować `ASC` lub `DESC`, aby wskazać kolejność rosnącą lub malejącą.</span><span class="sxs-lookup"><span data-stu-id="61ad5-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="61ad5-116">Oddziel wiele kolumn przecinkami.</span><span class="sxs-lookup"><span data-stu-id="61ad5-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="61ad5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="61ad5-117">Example</span></span>  
 <span data-ttu-id="61ad5-118">Poniższy przykład kodu ładuje dane z tabeli Customers przykładowej bazy danych Northwind do kontrolki <xref:System.Windows.Forms.DataGridView>, a następnie filtruje i sortuje wyświetlane dane.</span><span class="sxs-lookup"><span data-stu-id="61ad5-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61ad5-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="61ad5-119">Compiling the Code</span></span>  
 <span data-ttu-id="61ad5-120">Aby uruchomić ten przykład, wklej kod do formularza zawierającego <xref:System.Windows.Forms.BindingSource> o nazwie `BindingSource1` i <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="61ad5-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="61ad5-121">Obsłuż zdarzenie <xref:System.Windows.Forms.Form.Load> dla `InitializeSortedFilteredBindingSource` formularzy i wywołań w metodzie obsługi zdarzeń ładowania.</span><span class="sxs-lookup"><span data-stu-id="61ad5-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ad5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61ad5-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="61ad5-123">[Instrukcje: Instalowanie przykładowych baz danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="61ad5-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="61ad5-124">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="61ad5-124">BindingSource Component</span></span>](bindingsource-component.md)
