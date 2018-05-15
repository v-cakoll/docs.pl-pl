---
title: Jak powiązać z wynikami zapytania LINQ
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d374bb69b6b7e022497403b9591b27e9ad7e2395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="3636d-102">Jak powiązać z wynikami zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="3636d-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="3636d-103">W tym przykładzie pokazano, jak do uruchomienia zapytania LINQ, a następnie powiązać z wyników.</span><span class="sxs-lookup"><span data-stu-id="3636d-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3636d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3636d-104">Example</span></span>  
 <span data-ttu-id="3636d-105">Poniższy przykład tworzy dwa pola listy.</span><span class="sxs-lookup"><span data-stu-id="3636d-105">The following example creates two list boxes.</span></span> <span data-ttu-id="3636d-106">Pierwsze pole listy zawiera trzy elementy listy.</span><span class="sxs-lookup"><span data-stu-id="3636d-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="3636d-107">Zaznaczenie elementu w pierwszym polu listy wywołuje następujące programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3636d-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="3636d-108">W tym przykładzie `Tasks` jest kolekcją `Task` obiektów.</span><span class="sxs-lookup"><span data-stu-id="3636d-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="3636d-109">`Task` Klasa ma właściwości o nazwie `Priority`.</span><span class="sxs-lookup"><span data-stu-id="3636d-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="3636d-110">Zapytania LINQ, która zwraca zbiór działa ten program obsługi zdarzeń `Task` obiektów, które mają wartość priorytetu wybrany, a następnie ustawia który jako <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="3636d-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="3636d-111">Drugie pole listy jest powiązany z tej kolekcji, ponieważ jego <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ma wartość `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="3636d-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="3636d-112">W związku z tym Wyświetla zwracanej kolekcji (na podstawie `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="3636d-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3636d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3636d-113">See Also</span></span>  
 [<span data-ttu-id="3636d-114">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="3636d-114">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [<span data-ttu-id="3636d-115">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="3636d-115">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="3636d-116">Nowości w WPF w wersji 4.5</span><span class="sxs-lookup"><span data-stu-id="3636d-116">What's New in WPF Version 4.5</span></span>](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [<span data-ttu-id="3636d-117">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="3636d-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="3636d-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3636d-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
