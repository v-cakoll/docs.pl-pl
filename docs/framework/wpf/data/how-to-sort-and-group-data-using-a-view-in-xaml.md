---
title: Jak sortować i grupować dane przy użyciu widoku w XAML
description: Dowiedz się, jak utworzyć widok zbierania danych służący do grupowania, sortowania i filtrowania w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621681"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="e0e77-103">Jak sortować i grupować dane przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="e0e77-103">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="e0e77-104">Ten przykład pokazuje, jak utworzyć widok zbierania danych w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e0e77-104">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="e0e77-105">Widoki umożliwiają korzystanie z funkcji grupowania, sortowania, filtrowania i koncepcji bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="e0e77-105">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e77-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0e77-106">Example</span></span>  
 <span data-ttu-id="e0e77-107">W poniższym przykładzie zasób statyczny o nazwie *miejsc* został zdefiniowany jako *Kolekcja obiektów miejsc* , w których każdy obiekt *miejsca* zawiera nazwę miasta i stan.</span><span class="sxs-lookup"><span data-stu-id="e0e77-107">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="e0e77-108">Prefiks *src* jest mapowany do przestrzeni nazw, w której zdefiniowano *miejsce* źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e0e77-108">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="e0e77-109">Przedrostek *Menedżer SCM* mapuje do `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` i *dat* mapuje na `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` .</span><span class="sxs-lookup"><span data-stu-id="e0e77-109">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="e0e77-110">Poniższy przykład tworzy widok zbierania danych, który jest posortowany według nazwy miasta i pogrupowane według stanu.</span><span class="sxs-lookup"><span data-stu-id="e0e77-110">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="e0e77-111">Widok może być następnie źródłem powiązań, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e0e77-111">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="e0e77-112">W przypadku powiązań z danymi XML zdefiniowanymi w <xref:System.Windows.Data.XmlDataProvider> zasobie poprzedź nazwę XML symbolem @.</span><span class="sxs-lookup"><span data-stu-id="e0e77-112">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="e0e77-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0e77-113">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="e0e77-114">Pobierz domyślny widok kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="e0e77-114">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="e0e77-115">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="e0e77-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e0e77-116">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="e0e77-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
