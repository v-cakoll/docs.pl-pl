---
title: Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: f5312177b9f437d9b5474d38fca80db6fc45245b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123678"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="78cc7-102">Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model</span><span class="sxs-lookup"><span data-stu-id="78cc7-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="78cc7-103">Za pomocą [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) .NET Framework można zaimplementować wzorzec Model-View-View Model (MVVM) i udostępnić zestawy na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="78cc7-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="78cc7-104">MVVM jest wzorcem aplikacji, który izoluje interfejs użytkownika od podstawowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="78cc7-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="78cc7-105">Można wdrożyć model i wyświetlić klasy modelu w projekcie biblioteki klas przenośnych w programie Visual Studio 2012, a następnie utworzyć widoki, które są dostosowane dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="78cc7-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="78cc7-106">Takie podejście umożliwia zapisanie modelu danych i logiki biznesowej tylko raz i użycie tego kodu z .NET Framework, Silverlight, Windows Phone i Windows 8. x aplikacji ze sklepu, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="78cc7-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Pokazuje przenośną bibliotekę klas z zestawami udostępniania MVVM na różnych platformach.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="78cc7-108">Ten temat nie zawiera ogólnych informacji o wzorcu MVVM.</span><span class="sxs-lookup"><span data-stu-id="78cc7-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="78cc7-109">Zawiera on tylko informacje o sposobach używania przenośnej biblioteki klas do implementowania MVVM.</span><span class="sxs-lookup"><span data-stu-id="78cc7-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="78cc7-110">Aby uzyskać więcej informacji na temat MVVM, zobacz [Przewodnik Szybki Start MVVM przy użyciu biblioteki biblioteki Prism Library 5,0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="78cc7-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="78cc7-111">Klasy obsługujące MVVM</span><span class="sxs-lookup"><span data-stu-id="78cc7-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="78cc7-112">Jeśli obiektem docelowym jest .NET Framework 4,5, .NET dla aplikacji do sklepu Windows 8. x, Silverlight lub Windows Phone 7,5 dla projektu biblioteki klas przenośnych, do wdrożenia wzorca MVVM są dostępne następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="78cc7-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="78cc7-113">Klasa <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-114">Klasa <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-115">Klasa <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-116">Klasa <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-117">Klasa <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-118">Klasa <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-119">Klasa <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-120">Klasa <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-121">Klasa <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-122">Klasa <xref:System.Windows.Input.ICommand?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="78cc7-123">Wszystkie klasy w przestrzeni nazw <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="78cc7-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="78cc7-124">Implementowanie MVVM</span><span class="sxs-lookup"><span data-stu-id="78cc7-124">Implementing MVVM</span></span>
 <span data-ttu-id="78cc7-125">Aby zaimplementować MVVM, zazwyczaj tworzysz model i model widoku w projekcie biblioteki klas przenośnych, ponieważ projekt biblioteki klas przenośnych nie może odwoływać się do projektu nieprzenośnego.</span><span class="sxs-lookup"><span data-stu-id="78cc7-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="78cc7-126">Model i model widoku mogą znajdować się w tym samym projekcie lub w oddzielnych projektach.</span><span class="sxs-lookup"><span data-stu-id="78cc7-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="78cc7-127">Jeśli używasz oddzielnych projektów, Dodaj odwołanie z projektu modelu widoku do projektu modelu.</span><span class="sxs-lookup"><span data-stu-id="78cc7-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="78cc7-128">Po skompilowaniu modelu i wyświetleniu projektów modelu należy odwołać się do tych zestawów w aplikacji, która zawiera widok.</span><span class="sxs-lookup"><span data-stu-id="78cc7-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="78cc7-129">Jeśli widok współdziała tylko z modelem widoku, trzeba tylko odwołać się do zestawu, który zawiera model widoku.</span><span class="sxs-lookup"><span data-stu-id="78cc7-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="78cc7-130">Modelowanie</span><span class="sxs-lookup"><span data-stu-id="78cc7-130">Model</span></span>
 <span data-ttu-id="78cc7-131">W poniższym przykładzie przedstawiono uproszczoną klasę modelu, która może znajdować się w projekcie biblioteki klas przenośnych.</span><span class="sxs-lookup"><span data-stu-id="78cc7-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="78cc7-132">Poniższy przykład pokazuje prostą metodę wypełniania, pobierania i aktualizowania danych w projekcie biblioteki klas przenośnych.</span><span class="sxs-lookup"><span data-stu-id="78cc7-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="78cc7-133">W rzeczywistej aplikacji można pobrać dane ze źródła, takiego jak usługa Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="78cc7-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="78cc7-134">Wyświetl model</span><span class="sxs-lookup"><span data-stu-id="78cc7-134">View Model</span></span>
 <span data-ttu-id="78cc7-135">Klasa bazowa dla modeli widoków jest często dodawana podczas implementowania wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="78cc7-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="78cc7-136">Poniższy przykład pokazuje klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="78cc7-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="78cc7-137">Implementacja interfejsu <xref:System.Windows.Input.ICommand> jest często używana ze wzorcem MVVM.</span><span class="sxs-lookup"><span data-stu-id="78cc7-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="78cc7-138">W poniższym przykładzie przedstawiono implementację interfejsu <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="78cc7-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="78cc7-139">W poniższym przykładzie przedstawiono uproszczony model widoku.</span><span class="sxs-lookup"><span data-stu-id="78cc7-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="78cc7-140">Widok</span><span class="sxs-lookup"><span data-stu-id="78cc7-140">View</span></span>  
 <span data-ttu-id="78cc7-141">Z poziomu aplikacji .NET Framework 4,5, aplikacji do sklepu Windows 8. x, aplikacji opartej na technologii Silverlight lub Windows Phone 7,5 aplikacji można odwołać się do zestawu, który zawiera model i widok projektów modelu.</span><span class="sxs-lookup"><span data-stu-id="78cc7-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="78cc7-142">Następnie utworzysz widok, który współdziała z modelem widoku.</span><span class="sxs-lookup"><span data-stu-id="78cc7-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="78cc7-143">Poniższy przykład przedstawia uproszczoną aplikację Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="78cc7-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="78cc7-144">Możesz tworzyć podobne widoki w aplikacjach w sklepie Silverlight, Windows Phone lub Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="78cc7-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="78cc7-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78cc7-145">See also</span></span>

- [<span data-ttu-id="78cc7-146">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="78cc7-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
