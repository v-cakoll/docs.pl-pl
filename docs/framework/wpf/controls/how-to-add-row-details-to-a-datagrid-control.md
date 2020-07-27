---
title: 'Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid'
description: Dowiedz się, jak dostosować prezentację danych przy użyciu kontrolki DataGrid Windows Presentation Foundation, dodając sekcję Szczegóły wiersza.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164950"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="d0236-103">Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid</span><span class="sxs-lookup"><span data-stu-id="d0236-103">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="d0236-104">Korzystając z <xref:System.Windows.Controls.DataGrid> kontrolki, można dostosować prezentację danych, dodając sekcję Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="d0236-104">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="d0236-105">Dodanie sekcji Szczegóły wiersza umożliwia grupowanie niektórych danych w szablonie, który jest opcjonalnie widoczny lub zwinięty.</span><span class="sxs-lookup"><span data-stu-id="d0236-105">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="d0236-106">Na przykład można dodać Szczegóły wierszy do obiektu, <xref:System.Windows.Controls.DataGrid> który przedstawia tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid> , ale wyświetla więcej pól danych, gdy użytkownik wybierze wiersz.</span><span class="sxs-lookup"><span data-stu-id="d0236-106">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="d0236-107">Zdefiniuj szablon dla sekcji Szczegóły wiersza w <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d0236-107">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="d0236-108">Na poniższej ilustracji przedstawiono przykład sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="d0236-108">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="d0236-109">![Siatka danych wyświetlana z szczegółami wiersza](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="d0236-109">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="d0236-110">Szablon Szczegóły wiersza definiuje się jako wbudowany kod XAML lub jako zasób.</span><span class="sxs-lookup"><span data-stu-id="d0236-110">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="d0236-111">Oba podejścia przedstawiono w poniższych procedurach.</span><span class="sxs-lookup"><span data-stu-id="d0236-111">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="d0236-112">Szablon danych, który jest dodawany jako zasób, może być używany w całym projekcie bez ponownego tworzenia szablonu.</span><span class="sxs-lookup"><span data-stu-id="d0236-112">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="d0236-113">Szablon danych, który jest dodawany jako wbudowany kod XAML jest dostępny tylko z kontrolki, w której jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d0236-113">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="d0236-114">Aby wyświetlić szczegóły wiersza przy użyciu wbudowanego języka XAML</span><span class="sxs-lookup"><span data-stu-id="d0236-114">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="d0236-115">Utwórz <xref:System.Windows.Controls.DataGrid> , który wyświetla dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d0236-115">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="d0236-116">W <xref:System.Windows.Controls.DataGrid> elemencie Dodaj <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span><span class="sxs-lookup"><span data-stu-id="d0236-116">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="d0236-117">Utwórz <xref:System.Windows.DataTemplate> , który definiuje wygląd sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="d0236-117">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="d0236-118">Poniższy kod XAML przedstawia <xref:System.Windows.Controls.DataGrid> i sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowanej metody.</span><span class="sxs-lookup"><span data-stu-id="d0236-118">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="d0236-119"><xref:System.Windows.Controls.DataGrid>Po wybraniu wiersza wyświetlane są trzy wartości w każdym wierszu i trzy więcej wartości.</span><span class="sxs-lookup"><span data-stu-id="d0236-119">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="d0236-120">Poniższy kod przedstawia zapytanie, które jest używane do wybierania danych, które są wyświetlane w <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="d0236-120">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="d0236-121">W tym przykładzie zapytanie wybiera dane z jednostki, która zawiera informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="d0236-121">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="d0236-122">Aby wyświetlić szczegóły wiersza za pomocą zasobu</span><span class="sxs-lookup"><span data-stu-id="d0236-122">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="d0236-123">Utwórz <xref:System.Windows.Controls.DataGrid> , który wyświetla dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d0236-123">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="d0236-124">Dodaj <xref:System.Windows.FrameworkElement.Resources%2A> element do elementu głównego, takiego jak <xref:System.Windows.Window> kontrolka lub <xref:System.Windows.Controls.Page> kontrolka, lub Dodaj <xref:System.Windows.Application.Resources%2A> element do <xref:System.Windows.Application> klasy w pliku App. XAML (lub Application. XAML).</span><span class="sxs-lookup"><span data-stu-id="d0236-124">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="d0236-125">W elemencie Resources Utwórz, <xref:System.Windows.DataTemplate> który definiuje wygląd sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="d0236-125">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="d0236-126">Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w <xref:System.Windows.Application> klasie.</span><span class="sxs-lookup"><span data-stu-id="d0236-126">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="d0236-127">W <xref:System.Windows.DataTemplate> , ustaw dla [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) wartość, która jednoznacznie identyfikuje szablon danych.</span><span class="sxs-lookup"><span data-stu-id="d0236-127">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="d0236-128">W <xref:System.Windows.Controls.DataGrid> elemencie Ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> Właściwość na zasób zdefiniowany w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="d0236-128">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="d0236-129">Przypisz zasób jako zasób statyczny.</span><span class="sxs-lookup"><span data-stu-id="d0236-129">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="d0236-130">Poniższy kod XAML pokazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> Właściwość ustawioną dla zasobu z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="d0236-130">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="d0236-131">Aby ustawić widoczność i uniemożliwić przewijanie w poziomie dla szczegółów wiersza</span><span class="sxs-lookup"><span data-stu-id="d0236-131">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="d0236-132">W razie potrzeby ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> Właściwość na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> wartość.</span><span class="sxs-lookup"><span data-stu-id="d0236-132">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="d0236-133">Domyślnie wartość jest równa <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> .</span><span class="sxs-lookup"><span data-stu-id="d0236-133">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="d0236-134">Można ustawić, aby <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> wyświetlić szczegóły wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> ukryć szczegóły dla wszystkich wierszy.</span><span class="sxs-lookup"><span data-stu-id="d0236-134">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="d0236-135">W razie potrzeby ustaw <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> Właściwość na, `true` Aby zapobiec przewijaniu sekcji Szczegóły wiersza w poziomie.</span><span class="sxs-lookup"><span data-stu-id="d0236-135">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
