---
title: 'Instrukcje: Pobieranie widoku domyślnego kolekcji danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: 746331e69ee1e5eee795a0e35202f4889b72c53f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931527"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="05cae-102">Instrukcje: Pobieranie widoku domyślnego kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="05cae-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="05cae-103">Widoki zezwala na tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od tego, czy sortowanie, filtrowanie lub kryteria grupowania.</span><span class="sxs-lookup"><span data-stu-id="05cae-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="05cae-104">Każda kolekcja ma jeden udostępnionego widok domyślny, jest używany jako źródło faktycznego wiązania, gdy powiązanie Określa kolekcję jako źródło.</span><span class="sxs-lookup"><span data-stu-id="05cae-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="05cae-105">Ten przykład pokazuje, jak pobrać domyślny widok kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05cae-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05cae-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="05cae-106">Example</span></span>  
 <span data-ttu-id="05cae-107">Aby utworzyć widok, konieczne jest odwołanie do obiektu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05cae-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="05cae-108">Ten obiekt danych można uzyskać, odwołując się do własnego obiektu związanego z kodem, uzyskując kontekst danych, pobieranie właściwości źródła danych lub pobieranie właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="05cae-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="05cae-109">W tym przykładzie pokazano, jak uzyskać <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu danych i użyć go bezpośrednio uzyskać domyślnej kolekcji wyświetlić dla tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05cae-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="05cae-110">W tym przykładzie jest głównym elementem <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="05cae-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="05cae-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Ustawiono *myDataSource*, która odnosi się do dostawcy danych, który jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z *kolejności* obiektów.</span><span class="sxs-lookup"><span data-stu-id="05cae-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="05cae-112">Alternatywnie możesz utworzyć wystąpienia i powiązać z własną kolekcję widoku przy użyciu <xref:System.Windows.Data.CollectionViewSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="05cae-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="05cae-113">Ten widok kolekcji jest udostępniany tylko przez formanty, które należy powiązać go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="05cae-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="05cae-114">Aby uzyskać przykład, zobacz, jak do utworzenia widoku w temacie [Przegląd wiązanie danych](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="05cae-114">For an example, see the How to Create a View section in the [Data Binding Overview](data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="05cae-115">Przykłady funkcje udostępniane przez widok kolekcji, zobacz [sortowanie danych w widoku](how-to-sort-data-in-a-view.md), [filtrować dane w widoku](how-to-filter-data-in-a-view.md), i [przejdź do obiektów w danych CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="05cae-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](how-to-sort-data-in-a-view.md), [Filter Data in a View](how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05cae-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05cae-116">See also</span></span>

- [<span data-ttu-id="05cae-117">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="05cae-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="05cae-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="05cae-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
