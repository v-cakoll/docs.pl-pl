---
title: Jak dodać szczegóły wiersza do formantu DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559680"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="ffb86-102">Jak dodać szczegóły wiersza do formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="ffb86-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="ffb86-103">Korzystając z formantu <xref:System.Windows.Controls.DataGrid>, można dostosować prezentację danych, dodając sekcję Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="ffb86-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="ffb86-104">Dodanie sekcji Szczegóły wiersza umożliwia grupowanie niektórych danych w szablonie, który jest opcjonalnie widoczny lub zwinięty.</span><span class="sxs-lookup"><span data-stu-id="ffb86-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="ffb86-105">Na przykład można dodać Szczegóły wierszy do <xref:System.Windows.Controls.DataGrid>, które przedstawia tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>, ale wyświetla więcej pól danych, gdy użytkownik zaznaczy wiersz.</span><span class="sxs-lookup"><span data-stu-id="ffb86-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="ffb86-106">Szablon sekcji Szczegóły wiersza można zdefiniować we właściwości <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="ffb86-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="ffb86-107">Na poniższej ilustracji przedstawiono przykład sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="ffb86-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="ffb86-108">![Siatka danych wyświetlana z szczegółami wiersza](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="ffb86-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="ffb86-109">Szablon Szczegóły wiersza definiuje się jako wbudowany kod XAML lub jako zasób.</span><span class="sxs-lookup"><span data-stu-id="ffb86-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="ffb86-110">Oba podejścia przedstawiono w poniższych procedurach.</span><span class="sxs-lookup"><span data-stu-id="ffb86-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="ffb86-111">Szablon danych, który jest dodawany jako zasób, może być używany w całym projekcie bez ponownego tworzenia szablonu.</span><span class="sxs-lookup"><span data-stu-id="ffb86-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="ffb86-112">Szablon danych, który jest dodawany jako wbudowany kod XAML jest dostępny tylko z kontrolki, w której jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ffb86-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="ffb86-113">Aby wyświetlić szczegóły wiersza przy użyciu wbudowanego języka XAML</span><span class="sxs-lookup"><span data-stu-id="ffb86-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="ffb86-114">Utwórz <xref:System.Windows.Controls.DataGrid>, który wyświetla dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ffb86-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="ffb86-115">W <xref:System.Windows.Controls.DataGrid> elementu Dodawanie <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="ffb86-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="ffb86-116">Utwórz <xref:System.Windows.DataTemplate>, który definiuje wygląd sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="ffb86-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="ffb86-117">Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid> i sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowane.</span><span class="sxs-lookup"><span data-stu-id="ffb86-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="ffb86-118"><xref:System.Windows.Controls.DataGrid> wyświetla trzy wartości w każdym wierszu i trzy więcej wartości po zaznaczeniu wiersza.</span><span class="sxs-lookup"><span data-stu-id="ffb86-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="ffb86-119">Poniższy kod przedstawia zapytanie, które jest używane do wybierania danych, które są wyświetlane w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="ffb86-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="ffb86-120">W tym przykładzie zapytanie wybiera dane z jednostki, która zawiera informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="ffb86-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="ffb86-121">Aby wyświetlić szczegóły wiersza za pomocą zasobu</span><span class="sxs-lookup"><span data-stu-id="ffb86-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="ffb86-122">Utwórz <xref:System.Windows.Controls.DataGrid>, który wyświetla dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ffb86-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="ffb86-123">Dodaj element <xref:System.Windows.FrameworkElement.Resources%2A> do elementu głównego, takiego jak kontrolka <xref:System.Windows.Window> lub kontrolka <xref:System.Windows.Controls.Page> lub Dodaj element <xref:System.Windows.Application.Resources%2A> do klasy <xref:System.Windows.Application> w pliku App. XAML (lub Application. XAML).</span><span class="sxs-lookup"><span data-stu-id="ffb86-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="ffb86-124">W elemencie Resources Utwórz <xref:System.Windows.DataTemplate>, który definiuje wygląd sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="ffb86-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="ffb86-125">Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w klasie <xref:System.Windows.Application>.</span><span class="sxs-lookup"><span data-stu-id="ffb86-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="ffb86-126">Na <xref:System.Windows.DataTemplate>Ustaw dla [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) wartość, która jednoznacznie identyfikuje szablon danych.</span><span class="sxs-lookup"><span data-stu-id="ffb86-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="ffb86-127">W elemencie <xref:System.Windows.Controls.DataGrid> ustaw właściwość <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> na zasób zdefiniowany w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="ffb86-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="ffb86-128">Przypisz zasób jako zasób statyczny.</span><span class="sxs-lookup"><span data-stu-id="ffb86-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="ffb86-129">Poniższy kod XAML przedstawia Właściwość <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> ustawioną na zasób z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="ffb86-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="ffb86-130">Aby ustawić widoczność i uniemożliwić przewijanie w poziomie dla szczegółów wiersza</span><span class="sxs-lookup"><span data-stu-id="ffb86-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="ffb86-131">W razie potrzeby ustaw właściwość <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> na wartość <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>.</span><span class="sxs-lookup"><span data-stu-id="ffb86-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="ffb86-132">Domyślnie wartość jest ustawiona na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="ffb86-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="ffb86-133">Można ustawić <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>, aby wyświetlić szczegóły dla wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>, aby ukryć szczegóły dla wszystkich wierszy.</span><span class="sxs-lookup"><span data-stu-id="ffb86-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="ffb86-134">W razie potrzeby ustaw właściwość <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> na `true`, aby zapobiec przewijaniu sekcji Szczegóły wiersza w poziomie.</span><span class="sxs-lookup"><span data-stu-id="ffb86-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
