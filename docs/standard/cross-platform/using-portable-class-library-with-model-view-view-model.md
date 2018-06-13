---
title: Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model
ms.date: 03/30/2017
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
ms.openlocfilehash: aa8423c5c9453a9edb1058f0d5bdf4c494ece088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574111"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="efc05-102">Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model</span><span class="sxs-lookup"><span data-stu-id="efc05-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="efc05-103">Można użyć programu .NET Framework [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementacji wzorca Model-View-View Model (MVVM) i udostępnianie zestawów na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="efc05-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>  
  
 <span data-ttu-id="efc05-104">MVVM to wzorzec aplikacji, który wyodrębnia interfejsu użytkownika z podstawowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="efc05-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="efc05-105">Można wdrożyć modelu i widoku klasy modelu w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], a następnie Utwórz widoki, które są dostosowane dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="efc05-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], and then create views that are customized for different platforms.</span></span> <span data-ttu-id="efc05-106">Takie podejście umożliwia zapisać danych modelu i logiki biznesowej tylko raz, a następnie użyj tego kodu .NET Framework, Silverlight, Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="efc05-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="efc05-107">![Przenośne z modelem MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="efc05-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>  
  
 <span data-ttu-id="efc05-108">Ten temat nie zawiera ogólne informacje o wzorcu MVVM.</span><span class="sxs-lookup"><span data-stu-id="efc05-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="efc05-109">Zapewnia tylko informacje o sposobie używania [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] do zaimplementowania MVVM.</span><span class="sxs-lookup"><span data-stu-id="efc05-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="efc05-110">Aby uzyskać więcej informacji na temat MVVM, zobacz [szybkiego startu MVVM](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).</span><span class="sxs-lookup"><span data-stu-id="efc05-110">For more information about MVVM, see the [MVVM Quickstart](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).</span></span>  
  
## <a name="classes-that-support-mvvm"></a><span data-ttu-id="efc05-111">Klasy, które obsługują MVVM</span><span class="sxs-lookup"><span data-stu-id="efc05-111">Classes That Support MVVM</span></span>  
 <span data-ttu-id="efc05-112">Jeśli zostanie rozpoczęta [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, lub Windows Phone w wersji 7.5 dla Twojego [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, następujące klasy są dostępne w zakresie implementacji wzorca MVVM:</span><span class="sxs-lookup"><span data-stu-id="efc05-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>  
  
-   <span data-ttu-id="efc05-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Klasy</span><span class="sxs-lookup"><span data-stu-id="efc05-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="efc05-123">Wszystkie klasy w <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="efc05-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>  
  
## <a name="implementing-mvvm"></a><span data-ttu-id="efc05-124">Implementowanie MVVM</span><span class="sxs-lookup"><span data-stu-id="efc05-124">Implementing MVVM</span></span>  
 <span data-ttu-id="efc05-125">Aby zaimplementować MVVM, zwykle tworzenia modelu i model widoku w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, ponieważ [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu nie może odwoływać się nieprzenośny projekt.</span><span class="sxs-lookup"><span data-stu-id="efc05-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="efc05-126">Model i model widoku można w tym samym projekcie lub w oddzielnych projektów.</span><span class="sxs-lookup"><span data-stu-id="efc05-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="efc05-127">Jeśli używasz osobne projekty, Dodaj odwołanie z widoku projektu modelu do projektu modelu.</span><span class="sxs-lookup"><span data-stu-id="efc05-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>  
  
 <span data-ttu-id="efc05-128">Po skompilować model i przeglądać projekty modelu odwołują się te zestawy w aplikacji, która zawiera widok.</span><span class="sxs-lookup"><span data-stu-id="efc05-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="efc05-129">Jeśli widok współpracuje tylko z modelu widoku, wystarczy odwoływać się do zestawu, który zawiera model widoku.</span><span class="sxs-lookup"><span data-stu-id="efc05-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>  
  
### <a name="model"></a><span data-ttu-id="efc05-130">Model</span><span class="sxs-lookup"><span data-stu-id="efc05-130">Model</span></span>  
 <span data-ttu-id="efc05-131">W poniższym przykładzie pokazano uproszczony model klasy, która może znajdować się w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="efc05-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 <span data-ttu-id="efc05-132">W poniższym przykładzie przedstawiono prosty sposób wypełniania, pobierania i aktualizowania danych w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="efc05-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="efc05-133">W rzeczywistym aplikacji może pobrać danych ze źródła, takie jak usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="efc05-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a><span data-ttu-id="efc05-134">Model widoku</span><span class="sxs-lookup"><span data-stu-id="efc05-134">View Model</span></span>  
 <span data-ttu-id="efc05-135">Podczas implementowania wzorzec MVVM często dodawany jest klasą bazową dla modeli widoku.</span><span class="sxs-lookup"><span data-stu-id="efc05-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="efc05-136">W poniższym przykładzie przedstawiono klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="efc05-136">The following example shows a base class.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 <span data-ttu-id="efc05-137">Implementacja interfejsu <xref:System.Windows.Input.ICommand> interfejs jest często używany ze wzorcem MVVM.</span><span class="sxs-lookup"><span data-stu-id="efc05-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="efc05-138">Poniższy przykład przedstawia implementację <xref:System.Windows.Input.ICommand> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="efc05-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 <span data-ttu-id="efc05-139">W poniższym przykładzie pokazano uproszczony widok modelu.</span><span class="sxs-lookup"><span data-stu-id="efc05-139">The following example shows a simplified view model.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="efc05-140">Widok</span><span class="sxs-lookup"><span data-stu-id="efc05-140">View</span></span>  
 <span data-ttu-id="efc05-141">Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, oparte na technologii Silverlight aplikację lub aplikację systemu Windows Phone 7.5, możesz odwoływać się do zestawu, który zawiera projekty modelu modelu i widoku.</span><span class="sxs-lookup"><span data-stu-id="efc05-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="efc05-142">Następnie można utworzyć widoku, który współdziała z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="efc05-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="efc05-143">W poniższym przykładzie pokazano uproszczony aplikacji Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="efc05-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="efc05-144">Widoki podobnie można utworzyć w programie Silverlight, Windows Phone lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efc05-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="efc05-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efc05-145">See Also</span></span>  
 [<span data-ttu-id="efc05-146">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="efc05-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
