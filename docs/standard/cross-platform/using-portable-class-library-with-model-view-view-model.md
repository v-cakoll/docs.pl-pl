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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b48dc67e18411d82f03d29ab244d57575d6d720
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835788"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="ea8c6-102">Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model</span><span class="sxs-lookup"><span data-stu-id="ea8c6-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="ea8c6-103">Można użyć programu .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementacji wzorca Model-View-View Model (MVVM) i udostępnianie zestawów na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="ea8c6-104">MVVM jest wzorzec aplikacji, który izoluje w interfejsie użytkownika z podstawowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="ea8c6-105">Można wdrożyć modelu i widoku klasy modelu w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu w programie Visual Studio 2012, a następnie Utwórz widoki, które są dostosowywane na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="ea8c6-106">Dzięki temu można zapisać danych modelu i logikę biznesową tylko raz i użycia, ten kod z .NET Framework, Silverlight, Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>

 <span data-ttu-id="ea8c6-107">![Przenośne przy użyciu diagramu MVVM](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="ea8c6-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>

 <span data-ttu-id="ea8c6-108">Ten temat nie zawiera ogólne informacje dotyczące wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="ea8c6-109">Zapewnia tylko informacje o sposobie używania [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] do zaimplementowania MVVM.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="ea8c6-110">Aby uzyskać więcej informacji na temat MVVM zobacz [MVVM Szybki Start za pomocą biblioteki Prism 5.0 biblioteki dla WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="ea8c6-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="ea8c6-111">Klasy, które obsługują MVVM</span><span class="sxs-lookup"><span data-stu-id="ea8c6-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="ea8c6-112">Jeśli platformą docelową jest program [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight lub Windows Phone 7.5 dla Twojego [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, następujące klasy są dostępne do implementowania wzorca MVVM:</span><span class="sxs-lookup"><span data-stu-id="ea8c6-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>

-   <span data-ttu-id="ea8c6-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="ea8c6-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="ea8c6-123">Wszystkie klasy w <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ea8c6-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="ea8c6-124">Implementowanie MVVM</span><span class="sxs-lookup"><span data-stu-id="ea8c6-124">Implementing MVVM</span></span>
 <span data-ttu-id="ea8c6-125">Aby zaimplementować MVVM, zwykle tworzysz modelu i model widoku w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, ponieważ [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu nie może odwoływać się do projektu nieprzenośnych.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="ea8c6-126">Model i widoku modelu może być w tym samym projekcie lub w oddzielnych projektów.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="ea8c6-127">Użycie oddzielnych projektów, Dodaj odwołanie z projektu modelu widoku projektu modelu.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="ea8c6-128">Po skompilować model i wyświetlanie modelu projektów, możesz tych zestawów odwołań w aplikację, która zawiera widok.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="ea8c6-129">Jeśli widok współdziała tylko z modelu widoku, wystarczy odwołać się do zestawu, który zawiera model widoku.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="ea8c6-130">Model</span><span class="sxs-lookup"><span data-stu-id="ea8c6-130">Model</span></span>
 <span data-ttu-id="ea8c6-131">W poniższym przykładzie pokazano klasę uproszczony model, który może znajdować się w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="ea8c6-132">Poniższy przykład pokazuje prosty sposób wypełnić, pobieranie i aktualizowanie danych w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="ea8c6-133">W rzeczywistej aplikacji może pobrać dane ze źródła, takich jak usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ea8c6-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="ea8c6-134">Model widoku</span><span class="sxs-lookup"><span data-stu-id="ea8c6-134">View Model</span></span>
 <span data-ttu-id="ea8c6-135">Klasa bazowa dla modeli widoków często jest dodawany podczas implementowania wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="ea8c6-136">Poniższy przykład przedstawia klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="ea8c6-137">Implementacja <xref:System.Windows.Input.ICommand> interfejsu jest często używany przy użyciu wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="ea8c6-138">W poniższym przykładzie pokazano implementację <xref:System.Windows.Input.ICommand> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="ea8c6-139">Poniższy przykład pokazuje wzór uproszczony widok.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="ea8c6-140">Widok</span><span class="sxs-lookup"><span data-stu-id="ea8c6-140">View</span></span>  
 <span data-ttu-id="ea8c6-141">Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, aplikacji opartych na technologii Silverlight lub aplikacji Windows Phone 7.5 można odwoływać się zestaw, który zawiera projekty modelu i widoku modelu.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="ea8c6-142">Następnie utworzysz widok, który wchodzi w interakcję z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="ea8c6-143">Poniższy przykład przedstawia uproszczoną aplikację Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="ea8c6-144">Można utworzyć podobne widoki w programie Silverlight, Windows Phone lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea8c6-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ea8c6-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea8c6-145">See also</span></span>

- [<span data-ttu-id="ea8c6-146">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="ea8c6-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
