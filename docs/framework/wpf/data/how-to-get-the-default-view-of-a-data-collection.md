---
title: Jak pobrać domyślny widok kolekcji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459119"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="83ab2-102">Jak pobrać domyślny widok kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="83ab2-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="83ab2-103">Widoki umożliwiają wyświetlanie tych samych danych na różne sposoby, w zależności od sortowania, filtrowania lub kryteriów grupowania.</span><span class="sxs-lookup"><span data-stu-id="83ab2-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="83ab2-104">Każda kolekcja ma jeden współużytkowany widok domyślny, który jest używany jako rzeczywiste Źródło powiązania, gdy powiązanie Określa kolekcję jako źródło.</span><span class="sxs-lookup"><span data-stu-id="83ab2-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="83ab2-105">Ten przykład pokazuje, jak uzyskać domyślny widok kolekcji.</span><span class="sxs-lookup"><span data-stu-id="83ab2-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83ab2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="83ab2-106">Example</span></span>  
 <span data-ttu-id="83ab2-107">Aby utworzyć widok, potrzebujesz odwołania do obiektu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="83ab2-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="83ab2-108">Ten obiekt danych można uzyskać, odwołując się do własnego obiektu związanego z kodem, pobierając kontekst danych, pobierając Właściwość źródła danych lub pobierając właściwość powiązania.</span><span class="sxs-lookup"><span data-stu-id="83ab2-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="83ab2-109">Ten przykład pokazuje, jak uzyskać <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu danych i użyć go do bezpośredniego uzyskania domyślnego widoku kolekcji dla tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="83ab2-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="83ab2-110">W tym przykładzie element główny jest <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="83ab2-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="83ab2-111"><xref:System.Windows.FrameworkElement.DataContext%2A> jest ustawiona na wartość *webdatasource*, która odnosi się do dostawcy danych, który jest <xref:System.Collections.ObjectModel.ObservableCollection%601> obiektów *kolejności* .</span><span class="sxs-lookup"><span data-stu-id="83ab2-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="83ab2-112">Alternatywnie można utworzyć wystąpienie i utworzyć powiązanie z własnym widokiem kolekcji, korzystając z klasy <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="83ab2-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="83ab2-113">Ten widok kolekcji jest współużytkowany tylko przez formanty, które są bezpośrednio powiązane z nim.</span><span class="sxs-lookup"><span data-stu-id="83ab2-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="83ab2-114">Aby zapoznać się z przykładem, zobacz sekcję jak utworzyć widok w temacie [powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83ab2-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="83ab2-115">Aby zapoznać się z przykładami funkcji udostępnianych przez widok kolekcji, zobacz [Sortowanie danych w widoku](how-to-sort-data-in-a-view.md), [filtrowanie danych w widoku](how-to-filter-data-in-a-view.md)i [nawigowanie po obiektach w CollectionView danych](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="83ab2-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](how-to-sort-data-in-a-view.md), [Filter Data in a View](how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ab2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83ab2-116">See also</span></span>

- [<span data-ttu-id="83ab2-117">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="83ab2-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="83ab2-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="83ab2-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
