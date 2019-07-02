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
ms.openlocfilehash: b53be90764c6537fb27cb1b5ed781a68e69effa0
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504678"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="fa8db-102">Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model</span><span class="sxs-lookup"><span data-stu-id="fa8db-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="fa8db-103">Można użyć programu .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementacji wzorca Model-View-View Model (MVVM) i udostępnianie zestawów na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="fa8db-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="fa8db-104">MVVM jest wzorzec aplikacji, który izoluje w interfejsie użytkownika z podstawowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="fa8db-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="fa8db-105">Można zaimplementować klasy modelu modelu i widoku w projekcie biblioteki klas przenośnych w programie Visual Studio 2012, a następnie Utwórz widoki, które są dostosowywane na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="fa8db-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="fa8db-106">Dzięki temu można zapisać danych modelu i logikę biznesową tylko raz i użycia, ten kod z .NET Framework, Silverlight, Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="fa8db-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>

 ![Pokazuje Portable Class Library za pomocą zestawów RMS sharing MVVM między platformami.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="fa8db-108">Ten temat nie zawiera ogólne informacje dotyczące wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="fa8db-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="fa8db-109">Tylko zawiera informacje o sposobie używania biblioteki klas przenośnych do zaimplementowania MVVM.</span><span class="sxs-lookup"><span data-stu-id="fa8db-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="fa8db-110">Aby uzyskać więcej informacji na temat MVVM zobacz [MVVM Szybki Start za pomocą biblioteki Prism 5.0 biblioteki dla WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="fa8db-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="fa8db-111">Klasy, które obsługują MVVM</span><span class="sxs-lookup"><span data-stu-id="fa8db-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="fa8db-112">Gdy miejscem docelowym .NET Framework 4.5 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight lub Windows Phone 7.5 dla Twojego projektu Portable Class Library następujące klasy są dostępne do implementowania wzorca MVVM:</span><span class="sxs-lookup"><span data-stu-id="fa8db-112">When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="fa8db-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Klasa</span><span class="sxs-lookup"><span data-stu-id="fa8db-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="fa8db-123">Wszystkie klasy w <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="fa8db-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="fa8db-124">Implementowanie MVVM</span><span class="sxs-lookup"><span data-stu-id="fa8db-124">Implementing MVVM</span></span>
 <span data-ttu-id="fa8db-125">Aby zaimplementować MVVM, zwykle tworzenia modelu i model widoku w projekcie biblioteki klas przenośnych, ponieważ projekt przenośnej biblioteki klas nie może odwoływać się do projektu nieprzenośne.</span><span class="sxs-lookup"><span data-stu-id="fa8db-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="fa8db-126">Model i widoku modelu może być w tym samym projekcie lub w oddzielnych projektów.</span><span class="sxs-lookup"><span data-stu-id="fa8db-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="fa8db-127">Użycie oddzielnych projektów, Dodaj odwołanie z projektu modelu widoku projektu modelu.</span><span class="sxs-lookup"><span data-stu-id="fa8db-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="fa8db-128">Po skompilować model i wyświetlanie modelu projektów, możesz tych zestawów odwołań w aplikację, która zawiera widok.</span><span class="sxs-lookup"><span data-stu-id="fa8db-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="fa8db-129">Jeśli widok współdziała tylko z modelu widoku, wystarczy odwołać się do zestawu, który zawiera model widoku.</span><span class="sxs-lookup"><span data-stu-id="fa8db-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="fa8db-130">Model</span><span class="sxs-lookup"><span data-stu-id="fa8db-130">Model</span></span>
 <span data-ttu-id="fa8db-131">Poniższy przykład przedstawia klasę uproszczony model, który może znajdować się w projekcie biblioteki klas przenośnych.</span><span class="sxs-lookup"><span data-stu-id="fa8db-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="fa8db-132">Poniższy przykład pokazuje prosty sposób wypełnić, pobieranie i aktualizowanie danych w projekcie biblioteki klas przenośnych.</span><span class="sxs-lookup"><span data-stu-id="fa8db-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="fa8db-133">W rzeczywistej aplikacji może pobrać dane ze źródła, takich jak usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fa8db-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="fa8db-134">Model widoku</span><span class="sxs-lookup"><span data-stu-id="fa8db-134">View Model</span></span>
 <span data-ttu-id="fa8db-135">Klasa bazowa dla modeli widoków często jest dodawany podczas implementowania wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="fa8db-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="fa8db-136">Poniższy przykład przedstawia klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="fa8db-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="fa8db-137">Implementacja <xref:System.Windows.Input.ICommand> interfejsu jest często używany przy użyciu wzorca MVVM.</span><span class="sxs-lookup"><span data-stu-id="fa8db-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="fa8db-138">W poniższym przykładzie pokazano implementację <xref:System.Windows.Input.ICommand> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fa8db-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="fa8db-139">Poniższy przykład pokazuje wzór uproszczony widok.</span><span class="sxs-lookup"><span data-stu-id="fa8db-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="fa8db-140">Widok</span><span class="sxs-lookup"><span data-stu-id="fa8db-140">View</span></span>  
 <span data-ttu-id="fa8db-141">Z poziomu aplikacji .NET Framework 4.5 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, aplikacji opartych na technologii Silverlight lub aplikacji Windows Phone 7.5 można odwoływać się zestaw, który zawiera projekty modelu i widoku modelu.</span><span class="sxs-lookup"><span data-stu-id="fa8db-141">From a .NET Framework 4.5 app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="fa8db-142">Następnie utworzysz widok, który wchodzi w interakcję z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="fa8db-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="fa8db-143">Poniższy przykład przedstawia uproszczoną aplikację Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku.</span><span class="sxs-lookup"><span data-stu-id="fa8db-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="fa8db-144">Można utworzyć podobne widoki w programie Silverlight, Windows Phone lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fa8db-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fa8db-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa8db-145">See also</span></span>

- [<span data-ttu-id="fa8db-146">Biblioteka klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="fa8db-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
