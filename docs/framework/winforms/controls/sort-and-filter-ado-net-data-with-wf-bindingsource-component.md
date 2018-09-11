---
title: 'Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows'
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
ms.openlocfilehash: 932d30d356225d88d7ef149561cc4c5cc8ac4dd0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271052"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="83093-102">Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83093-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="83093-103">Należy udostępnić sortowanie i filtrowanie możliwości <xref:System.Windows.Forms.BindingSource> kontrolować za pośrednictwem <xref:System.Windows.Forms.BindingSource.Sort%2A> i <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="83093-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="83093-104">Można zastosować proste sortowania, jeśli bazowe źródło danych jest <xref:System.ComponentModel.IBindingList>, i można zastosować filtrowanie zaawansowane, sortowanie, gdy źródłem danych jest <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="83093-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="83093-105"><xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość wymaga standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] Składnia: ciąg reprezentujący nazwę kolumny danych w źródle danych następuje `ASC` lub `DESC` do wskazania, czy lista powinny być sortowane w kolejności rosnącej lub malejącej.</span><span class="sxs-lookup"><span data-stu-id="83093-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="83093-106">Możesz ustawić zaawansowane sortowania lub wiele kolumn, sortowanie, rozdzielając każda kolumna przecinka jako separatora.</span><span class="sxs-lookup"><span data-stu-id="83093-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="83093-107"><xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość przyjmuje wyrażenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="83093-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83093-108">Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83093-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="83093-109">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="83093-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="83093-110">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="83093-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="83093-111">Aby filtrować dane przy użyciu kontrolki BindingSource</span><span class="sxs-lookup"><span data-stu-id="83093-111">To filter data with the BindingSource</span></span>  
  
-   <span data-ttu-id="83093-112">Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości do wyrażenia, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="83093-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="83093-113">W poniższym przykładzie kodu wyrażenie jest nazwa kolumny, a następnie wartość, która ma kolumny.</span><span class="sxs-lookup"><span data-stu-id="83093-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="83093-114">Aby posortować dane przy użyciu kontrolki BindingSource</span><span class="sxs-lookup"><span data-stu-id="83093-114">To sort data with the BindingSource</span></span>  
  
1.  <span data-ttu-id="83093-115">Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość na nazwę kolumny, która ma następuje `ASC` lub `DESC` do wskazania kolejności rosnącej lub malejącej.</span><span class="sxs-lookup"><span data-stu-id="83093-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2.  <span data-ttu-id="83093-116">Wiele kolumn należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="83093-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="83093-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="83093-117">Example</span></span>  
 <span data-ttu-id="83093-118">Poniższy przykładowy kod ładuje dane z tabeli Klienci w bazie danych Northwind do <xref:System.Windows.Forms.DataGridView> kontrolować, filtry i sortuje wyświetlanych danych.</span><span class="sxs-lookup"><span data-stu-id="83093-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83093-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="83093-119">Compiling the Code</span></span>  
 <span data-ttu-id="83093-120">Aby uruchomić ten przykład, Wklej kod do formularza, który zawiera <xref:System.Windows.Forms.BindingSource> o nazwie `BindingSource1` i <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="83093-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="83093-121">Obsługa <xref:System.Windows.Forms.Form.Load> zdarzenie w formularzu i wywołania `InitializeSortedFilteredBindingSource` w metodzie obsługi zdarzenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="83093-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83093-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83093-122">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [<span data-ttu-id="83093-123">Porady: Instalowanie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="83093-123">How to: Install Sample Databases</span></span>](https://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [<span data-ttu-id="83093-124">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="83093-124">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
