---
title: "Jak sortować i grupować dane przy użyciu widoku w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c219def87e258a2c9fc1bf4f4867287e6156c59a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="b4cc3-102">Jak sortować i grupować dane przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="b4cc3-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="b4cc3-103">W tym przykładzie pokazano, jak utworzyć widok kolekcji danych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4cc3-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="b4cc3-104">Widoki pozwalają funkcje grupowanie, sortowanie, filtrowanie i podstawowe pojęcie w zakresie bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="b4cc3-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4cc3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4cc3-105">Example</span></span>  
 <span data-ttu-id="b4cc3-106">W poniższym przykładzie statycznych zasobów o nazwie *umieszcza* jest zdefiniowany jako kolekcja *miejsce* obiektów, w których każdy *miejsce* obiektu jest obejmował nazwę miejscowości i Stan.</span><span class="sxs-lookup"><span data-stu-id="b4cc3-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="b4cc3-107">Prefiks *src* jest zamapowany do przestrzeni nazw gdzie źródła danych *miejsca* jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b4cc3-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="b4cc3-108">Prefiks *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="b4cc3-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="b4cc3-109">Poniższy przykład tworzy widok sortowane według nazwy mieście i w rozbiciu na stan zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="b4cc3-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="b4cc3-110">Widok można następnie źródle powiązania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b4cc3-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="b4cc3-111">Dla powiązań do danych XML zdefiniowane w <xref:System.Windows.Data.XmlDataProvider> zasobów, należy poprzedzić nazwę XML znaku @.</span><span class="sxs-lookup"><span data-stu-id="b4cc3-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="b4cc3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4cc3-112">See Also</span></span>  
 <xref:System.Windows.Data.CollectionViewSource>  
 [<span data-ttu-id="b4cc3-113">Pobierz widok domyślny zbierania danych</span><span class="sxs-lookup"><span data-stu-id="b4cc3-113">Get the Default View of a Data Collection</span></span>](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [<span data-ttu-id="b4cc3-114">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="b4cc3-114">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="b4cc3-115">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="b4cc3-115">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
