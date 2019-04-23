---
title: 'Instrukcje: Sortowanie i grupowanie danych przy użyciu widoku w XAML'
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
ms.openlocfilehash: ca4439b574264ebebfda745f0765f750099bc95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144524"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="e0cff-102">Instrukcje: Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="e0cff-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="e0cff-103">W tym przykładzie pokazano, jak utworzyć widok kolekcji danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0cff-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="e0cff-104">Widoki umożliwiają funkcje grupowania, sortowanie, filtrowanie i pojęcie bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="e0cff-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0cff-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0cff-105">Example</span></span>  
 <span data-ttu-id="e0cff-106">W poniższym przykładzie statycznych zasobów o nazwie *umieszcza* jest zdefiniowany jako kolekcja *miejscu* obiektów, w których każdy *miejscu* obiektu jest obejmowało nazwę miejscowości i Stan.</span><span class="sxs-lookup"><span data-stu-id="e0cff-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="e0cff-107">Prefiks *src* jest zamapowana na przestrzeń nazw gdzie źródło danych *miejsc* jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="e0cff-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="e0cff-108">Prefiks *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="e0cff-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="e0cff-109">Poniższy przykład tworzy widok zbierania danych, które są sortowane według nazwy miasta i pogrupowane według stanu.</span><span class="sxs-lookup"><span data-stu-id="e0cff-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="e0cff-110">Widok można następnie źródło powiązania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e0cff-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="e0cff-111">Dla powiązań z danymi XML zdefiniowane w <xref:System.Windows.Data.XmlDataProvider> zasobu, poprzedź nazwę XML przy użyciu znaku @.</span><span class="sxs-lookup"><span data-stu-id="e0cff-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="e0cff-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0cff-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="e0cff-113">Pobieranie widoku domyślnego kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="e0cff-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="e0cff-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="e0cff-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="e0cff-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e0cff-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
