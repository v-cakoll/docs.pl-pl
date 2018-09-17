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
ms.openlocfilehash: d2f07e471d4f0173f768b0d2a463d756b5be0682
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964962"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="30287-102">Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model</span><span class="sxs-lookup"><span data-stu-id="30287-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="30287-103">Można użyć programu .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementacji wzorca Model-View-View Model (MVVM) i udostępnianie zestawów na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="30287-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="30287-104">MVVM jest wzorzec aplikacji, który izoluje w interfejsie użytkownika z podstawowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="30287-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="30287-105">Można wdrożyć modelu i widoku klasy modelu w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], a następnie Utwórz widoki, które są dostosowywane na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="30287-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], and then create views that are customized for different platforms.</span></span> <span data-ttu-id="30287-106">Dzięki temu można zapisać danych modelu i logikę biznesową tylko raz i użycia, ten kod z .NET Framework, Silverlight, Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="30287-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="30287-107">![Przenośne przy użyciu diagramu MVVM](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="30287-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>  
  
 <span data-ttu-id="30287-108">Ten temat nie zawiera ogólne informacje dotyczące wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="30287-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="30287-109">Zapewnia tylko informacje o sposobie używania [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] do zaimplementowania MVVM.</span><span class="sxs-lookup"><span data-stu-id="30287-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="30287-110">Aby uzyskać więcej informacji na temat MVVM zobacz [Szybki Start MVVM](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).</span><span class="sxs-lookup"><span data-stu-id="30287-110">For more information about MVVM, see the [MVVM Quickstart](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).</span></span>  
  
## <a name="classes-that-support-mvvm"></a><span data-ttu-id="30287-111">Klasy, które obsługują MVVM</span><span class="sxs-lookup"><span data-stu-id="30287-111">Classes That Support MVVM</span></span>  
 <span data-ttu-id="30287-112">Jeśli platformą docelową jest program [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight lub Windows Phone 7.5 dla Twojego [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, następujące klasy są dostępne do implementowania wzorca MVVM:</span><span class="sxs-lookup"><span data-stu-id="30287-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>  
  
-   <span data-ttu-id="30287-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="30287-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="30287-123">Wszystkie klasy w <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="30287-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>  
  
## <a name="implementing-mvvm"></a><span data-ttu-id="30287-124">Implementowanie MVVM</span><span class="sxs-lookup"><span data-stu-id="30287-124">Implementing MVVM</span></span>  
 <span data-ttu-id="30287-125">Aby zaimplementować MVVM, zwykle tworzysz modelu i model widoku w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, ponieważ [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu nie może odwoływać się do projektu nieprzenośnych.</span><span class="sxs-lookup"><span data-stu-id="30287-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="30287-126">Model i widoku modelu może być w tym samym projekcie lub w oddzielnych projektów.</span><span class="sxs-lookup"><span data-stu-id="30287-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="30287-127">Użycie oddzielnych projektów, Dodaj odwołanie z projektu modelu widoku projektu modelu.</span><span class="sxs-lookup"><span data-stu-id="30287-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>  
  
 <span data-ttu-id="30287-128">Po skompilować model i wyświetlanie modelu projektów, możesz tych zestawów odwołań w aplikację, która zawiera widok.</span><span class="sxs-lookup"><span data-stu-id="30287-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="30287-129">Jeśli widok współdziała tylko z modelu widoku, wystarczy odwołać się do zestawu, który zawiera model widoku.</span><span class="sxs-lookup"><span data-stu-id="30287-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>  
  
### <a name="model"></a><span data-ttu-id="30287-130">Model</span><span class="sxs-lookup"><span data-stu-id="30287-130">Model</span></span>  
 <span data-ttu-id="30287-131">W poniższym przykładzie pokazano klasę uproszczony model, który może znajdować się w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="30287-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 <span data-ttu-id="30287-132">Poniższy przykład pokazuje prosty sposób wypełnić, pobieranie i aktualizowanie danych w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="30287-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="30287-133">W rzeczywistej aplikacji może pobrać dane ze źródła, takich jak usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="30287-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a><span data-ttu-id="30287-134">Model widoku</span><span class="sxs-lookup"><span data-stu-id="30287-134">View Model</span></span>  
 <span data-ttu-id="30287-135">Klasa bazowa dla modeli widoków często jest dodawany podczas implementowania wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="30287-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="30287-136">Poniższy przykład przedstawia klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="30287-136">The following example shows a base class.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 <span data-ttu-id="30287-137">Implementacja <xref:System.Windows.Input.ICommand> interfejsu jest często używany przy użyciu wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="30287-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="30287-138">W poniższym przykładzie pokazano implementację <xref:System.Windows.Input.ICommand> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="30287-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 <span data-ttu-id="30287-139">Poniższy przykład pokazuje wzór uproszczony widok.</span><span class="sxs-lookup"><span data-stu-id="30287-139">The following example shows a simplified view model.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="30287-140">Widok</span><span class="sxs-lookup"><span data-stu-id="30287-140">View</span></span>  
 <span data-ttu-id="30287-141">Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, aplikacji opartych na technologii Silverlight lub aplikacji Windows Phone 7.5 można odwoływać się zestaw, który zawiera projekty modelu i widoku modelu.</span><span class="sxs-lookup"><span data-stu-id="30287-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="30287-142">Następnie utworzysz widok, który wchodzi w interakcję z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="30287-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="30287-143">Poniższy przykład przedstawia uproszczoną aplikację Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="30287-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="30287-144">Można utworzyć podobne widoki w programie Silverlight, Windows Phone lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30287-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="30287-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30287-145">See also</span></span>

- [<span data-ttu-id="30287-146">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="30287-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
