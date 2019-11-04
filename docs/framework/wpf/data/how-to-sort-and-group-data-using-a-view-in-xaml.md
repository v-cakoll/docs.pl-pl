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
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460127"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="8d478-102">Jak sortować i grupować dane przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="8d478-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="8d478-103">Ten przykład pokazuje, jak utworzyć widok zbierania danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d478-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="8d478-104">Widoki umożliwiają korzystanie z funkcji grupowania, sortowania, filtrowania i koncepcji bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="8d478-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d478-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d478-105">Example</span></span>  
 <span data-ttu-id="8d478-106">W poniższym przykładzie zasób statyczny o nazwie *miejsc* został zdefiniowany jako *Kolekcja obiektów miejsc* , w których każdy obiekt *miejsca* zawiera nazwę miasta i stan.</span><span class="sxs-lookup"><span data-stu-id="8d478-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="8d478-107">Prefiks *src* jest mapowany do przestrzeni nazw, w której zdefiniowano *miejsce* źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8d478-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="8d478-108">Przedrostek *Menedżer SCM* mapuje do `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje do `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="8d478-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="8d478-109">Poniższy przykład tworzy widok zbierania danych, który jest posortowany według nazwy miasta i pogrupowane według stanu.</span><span class="sxs-lookup"><span data-stu-id="8d478-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="8d478-110">Widok może być następnie źródłem powiązań, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8d478-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="8d478-111">W przypadku powiązań z danymi XML zdefiniowanymi w zasobie <xref:System.Windows.Data.XmlDataProvider> poprzedź nazwę XML znakiem @.</span><span class="sxs-lookup"><span data-stu-id="8d478-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="8d478-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d478-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="8d478-113">Pobieranie widoku domyślnego kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="8d478-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="8d478-114">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="8d478-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8d478-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8d478-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
