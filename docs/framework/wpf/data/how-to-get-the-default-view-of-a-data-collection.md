---
title: 'Instrukcje: Pobierz domyślny widok kolekcji danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: 386c25998c85de2f674200fe7d269ae2fdabd72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588408"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="5b182-102">Instrukcje: Pobierz domyślny widok kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="5b182-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="5b182-103">Widoki zezwala na tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od tego, czy sortowanie, filtrowanie lub kryteria grupowania.</span><span class="sxs-lookup"><span data-stu-id="5b182-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="5b182-104">Każda kolekcja ma jeden udostępnionego widok domyślny, jest używany jako źródło faktycznego wiązania, gdy powiązanie Określa kolekcję jako źródło.</span><span class="sxs-lookup"><span data-stu-id="5b182-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="5b182-105">Ten przykład pokazuje, jak pobrać domyślny widok kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5b182-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b182-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b182-106">Example</span></span>  
 <span data-ttu-id="5b182-107">Aby utworzyć widok, konieczne jest odwołanie do obiektu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5b182-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="5b182-108">Ten obiekt danych można uzyskać, odwołując się do własnego obiektu związanego z kodem, uzyskując kontekst danych, pobieranie właściwości źródła danych lub pobieranie właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="5b182-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="5b182-109">W tym przykładzie pokazano, jak uzyskać <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu danych i użyć go bezpośrednio uzyskać domyślnej kolekcji wyświetlić dla tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5b182-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="5b182-110">W tym przykładzie jest głównym elementem <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="5b182-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="5b182-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Ustawiono *myDataSource*, która odnosi się do dostawcy danych, który jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z *kolejności* obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b182-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="5b182-112">Alternatywnie możesz utworzyć wystąpienia i powiązać z własną kolekcję widoku przy użyciu <xref:System.Windows.Data.CollectionViewSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="5b182-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="5b182-113">Ten widok kolekcji jest udostępniany tylko przez formanty, które należy powiązać go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="5b182-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="5b182-114">Aby uzyskać przykład, zobacz, jak do utworzenia widoku w temacie [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5b182-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="5b182-115">Przykłady funkcje udostępniane przez widok kolekcji, zobacz [sortowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrować dane w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), i [przejdź do obiektów w danych CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="5b182-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b182-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b182-116">See also</span></span>
- [<span data-ttu-id="5b182-117">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="5b182-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="5b182-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="5b182-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
