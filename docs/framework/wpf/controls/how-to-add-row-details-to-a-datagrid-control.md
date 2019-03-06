---
title: 'Instrukcje: Dodać szczegóły wiersza do formantu DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 5976e834ca984a257e5562b2a3c8051f45575f5b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372194"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="dac9e-102">Instrukcje: Dodać szczegóły wiersza do formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="dac9e-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="dac9e-103">Korzystając z <xref:System.Windows.Controls.DataGrid> kontrolki, prezentacji danych można dostosować, dodając sekcji Szczegóły wiersza.</span><span class="sxs-lookup"><span data-stu-id="dac9e-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="dac9e-104">Dodawanie sekcji Szczegóły wiersza umożliwiają grupowanie niektóre dane w szablonie, który jest opcjonalnie widoczny czy zwinięty.</span><span class="sxs-lookup"><span data-stu-id="dac9e-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="dac9e-105">Na przykład można dodać szczegóły wiersza do <xref:System.Windows.Controls.DataGrid> przedstawiające tylko podsumowanie danych dla każdego wiersza w <xref:System.Windows.Controls.DataGrid>, ale zabezpieczeniem więcej pól danych, gdy użytkownik wybierze wiersz.</span><span class="sxs-lookup"><span data-stu-id="dac9e-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="dac9e-106">Zdefiniuj szablon dla sekcji Szczegóły wiersza w <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dac9e-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="dac9e-107">Na poniższej ilustracji przedstawiono przykład sekcji szczegółów wiersza.</span><span class="sxs-lookup"><span data-stu-id="dac9e-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="dac9e-108">![DataGrid, przedstawiono szczegóły wiersza](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="dac9e-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="dac9e-109">Należy zdefiniować szablon szczegóły wiersza, jako jako wbudowane XAML lub zasobu.</span><span class="sxs-lookup"><span data-stu-id="dac9e-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="dac9e-110">Oba podejścia są wyświetlane w poniższych procedurach.</span><span class="sxs-lookup"><span data-stu-id="dac9e-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="dac9e-111">Szablon danych, który jest dodawany jako zasób może służyć w całym projekcie, bez potrzeby ponownego tworzenia szablonu.</span><span class="sxs-lookup"><span data-stu-id="dac9e-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="dac9e-112">Szablon danych, który jest dodawany jako wbudowane XAML jest dostępny tylko z formantu którym jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="dac9e-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="dac9e-113">Aby wyświetlić szczegóły wiersza przy użyciu wbudowanego XAML</span><span class="sxs-lookup"><span data-stu-id="dac9e-113">To display row details by using inline XAML</span></span>  
  
1.  <span data-ttu-id="dac9e-114">Utwórz <xref:System.Windows.Controls.DataGrid> wyświetlającą dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="dac9e-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="dac9e-115">W <xref:System.Windows.Controls.DataGrid> elementu Dodawanie <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="dac9e-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3.  <span data-ttu-id="dac9e-116">Utwórz <xref:System.Windows.DataTemplate> która definiuje wygląd elementów w sekcji szczegółów wiersza.</span><span class="sxs-lookup"><span data-stu-id="dac9e-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="dac9e-117">Pokazano w poniższym XAML <xref:System.Windows.Controls.DataGrid> oraz sposób definiowania <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="dac9e-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="dac9e-118"><xref:System.Windows.Controls.DataGrid> Wyświetla trzy wartości w każdym wierszu i trzy więcej wartości po zaznaczeniu wiersza.</span><span class="sxs-lookup"><span data-stu-id="dac9e-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="dac9e-119">Poniższy kod przedstawia zapytanie, które służy do wybierania danych, która jest wyświetlana w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="dac9e-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="dac9e-120">W tym przykładzie zapytanie wybiera dane z jednostki zawierającej informacje o kliencie.</span><span class="sxs-lookup"><span data-stu-id="dac9e-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="dac9e-121">Aby wyświetlić szczegóły wiersza przy użyciu zasobów</span><span class="sxs-lookup"><span data-stu-id="dac9e-121">To display row details by using a resource</span></span>  
  
1.  <span data-ttu-id="dac9e-122">Utwórz <xref:System.Windows.Controls.DataGrid> wyświetlającą dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="dac9e-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="dac9e-123">Dodaj <xref:System.Windows.FrameworkElement.Resources%2A> element do elementu głównego takich jak <xref:System.Windows.Window> kontroli lub <xref:System.Windows.Controls.Page> kontrolować lub dodać <xref:System.Windows.Application.Resources%2A> elementu <xref:System.Windows.Application> klasy w pliku App.xaml (lub Application.xaml).</span><span class="sxs-lookup"><span data-stu-id="dac9e-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3.  <span data-ttu-id="dac9e-124">W elemencie resources Utwórz <xref:System.Windows.DataTemplate> która definiuje wygląd elementów w sekcji szczegółów wiersza.</span><span class="sxs-lookup"><span data-stu-id="dac9e-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="dac9e-125">Pokazano w poniższym XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> zdefiniowane w <xref:System.Windows.Application> klasy.</span><span class="sxs-lookup"><span data-stu-id="dac9e-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <span data-ttu-id="dac9e-126">Na <xref:System.Windows.DataTemplate>ustaw [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) wartość, która jednoznacznie identyfikuje szablon danych.</span><span class="sxs-lookup"><span data-stu-id="dac9e-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5.  <span data-ttu-id="dac9e-127">W <xref:System.Windows.Controls.DataGrid> elementu, ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwości zasobu, zdefiniowane w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="dac9e-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="dac9e-128">Przypisuje zasób jako zasób statyczny.</span><span class="sxs-lookup"><span data-stu-id="dac9e-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="dac9e-129">Pokazano w poniższym XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> właściwością do zasobu z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="dac9e-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="dac9e-130">Aby ustawić widoczność i zapobiec przewijanie w poziomie dla szczegółów wiersza</span><span class="sxs-lookup"><span data-stu-id="dac9e-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1.  <span data-ttu-id="dac9e-131">Jeśli to konieczne, ustaw <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> właściwości <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> wartość.</span><span class="sxs-lookup"><span data-stu-id="dac9e-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="dac9e-132">Domyślnie ta wartość jest równa <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="dac9e-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="dac9e-133">Możesz ustawić na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> Aby wyświetlić szczegółowe informacje dla wszystkich wierszy lub <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> na razie ukryć szczegóły we wszystkich wierszach.</span><span class="sxs-lookup"><span data-stu-id="dac9e-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2.  <span data-ttu-id="dac9e-134">Jeśli to konieczne, ustaw <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> właściwość `true` zapobiegające wiersza szczegółów sekcji przewijanie w poziomie.</span><span class="sxs-lookup"><span data-stu-id="dac9e-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
