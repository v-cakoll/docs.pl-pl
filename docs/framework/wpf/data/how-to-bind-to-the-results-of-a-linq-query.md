---
title: "Jak powiązać z wynikami zapytania LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad4969d80f7bd801ec738fa40e8b2d4ab9deefad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="77615-102">Jak powiązać z wynikami zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="77615-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="77615-103">W tym przykładzie pokazano, jak do uruchomienia zapytania LINQ, a następnie powiązać z wyników.</span><span class="sxs-lookup"><span data-stu-id="77615-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77615-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="77615-104">Example</span></span>  
 <span data-ttu-id="77615-105">Poniższy przykład tworzy dwa pola listy.</span><span class="sxs-lookup"><span data-stu-id="77615-105">The following example creates two list boxes.</span></span> <span data-ttu-id="77615-106">Pierwsze pole listy zawiera trzy elementy listy.</span><span class="sxs-lookup"><span data-stu-id="77615-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="77615-107">Zaznaczenie elementu w pierwszym polu listy wywołuje następujące programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="77615-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="77615-108">W tym przykładzie `Tasks` jest kolekcją `Task` obiektów.</span><span class="sxs-lookup"><span data-stu-id="77615-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="77615-109">`Task` Klasa ma właściwości o nazwie `Priority`.</span><span class="sxs-lookup"><span data-stu-id="77615-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="77615-110">Zapytania LINQ, która zwraca zbiór działa ten program obsługi zdarzeń `Task` obiektów, które mają wartość priorytetu wybrany, a następnie ustawia który jako <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="77615-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="77615-111">Drugie pole listy jest powiązany z tej kolekcji, ponieważ jego <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ma wartość `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="77615-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="77615-112">W związku z tym Wyświetla zwracanej kolekcji (na podstawie `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="77615-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77615-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77615-113">See Also</span></span>  
 [<span data-ttu-id="77615-114">Udostępnianie danych do powiązania w XAML</span><span class="sxs-lookup"><span data-stu-id="77615-114">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [<span data-ttu-id="77615-115">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="77615-115">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="77615-116">Nowości w WPF w wersji 4.5</span><span class="sxs-lookup"><span data-stu-id="77615-116">What's New in WPF Version 4.5</span></span>](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [<span data-ttu-id="77615-117">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="77615-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="77615-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="77615-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
