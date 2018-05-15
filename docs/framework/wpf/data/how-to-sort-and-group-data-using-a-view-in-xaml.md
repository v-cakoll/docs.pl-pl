---
title: Jak sortować i grupować dane przy użyciu widoku w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="c076c-102">Jak sortować i grupować dane przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="c076c-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="c076c-103">W tym przykładzie pokazano, jak utworzyć widok kolekcji danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c076c-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="c076c-104">Widoki pozwalają funkcje grupowanie, sortowanie, filtrowanie i podstawowe pojęcie w zakresie bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="c076c-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c076c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c076c-105">Example</span></span>  
 <span data-ttu-id="c076c-106">W poniższym przykładzie statycznych zasobów o nazwie *umieszcza* jest zdefiniowany jako kolekcja *miejsce* obiektów, w których każdy *miejsce* obiektu jest obejmował nazwę miejscowości i Stan.</span><span class="sxs-lookup"><span data-stu-id="c076c-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="c076c-107">Prefiks *src* jest zamapowany do przestrzeni nazw gdzie źródła danych *miejsca* jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="c076c-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="c076c-108">Prefiks *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="c076c-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="c076c-109">Poniższy przykład tworzy widok sortowane według nazwy mieście i w rozbiciu na stan zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="c076c-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="c076c-110">Widok można następnie źródle powiązania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c076c-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="c076c-111">Dla powiązań do danych XML zdefiniowane w <xref:System.Windows.Data.XmlDataProvider> zasobów, należy poprzedzić nazwę XML znaku @.</span><span class="sxs-lookup"><span data-stu-id="c076c-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="c076c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c076c-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="c076c-113">Pobieranie widoku domyślnego kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="c076c-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="c076c-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="c076c-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c076c-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c076c-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
