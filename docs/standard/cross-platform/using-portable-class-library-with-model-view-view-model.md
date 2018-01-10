---
title: "Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc12a90025a1862fc6c588fe4425f3f8341da313
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model
Można użyć programu .NET Framework [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementacji wzorca Model-View-View Model (MVVM) i udostępnianie zestawów na wielu platformach.  
  
 MVVM to wzorzec aplikacji, który wyodrębnia interfejsu użytkownika z podstawowej logiki biznesowej. Można wdrożyć modelu i widoku klasy modelu w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], a następnie Utwórz widoki, które są dostosowane dla różnych platform. Takie podejście umożliwia zapisać danych modelu i logiki biznesowej tylko raz, a następnie użyj tego kodu .NET Framework, Silverlight, Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak pokazano na poniższej ilustracji.  
  
 ![Przenośne z modelem MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 Ten temat nie zawiera ogólne informacje o wzorcu MVVM. Zapewnia tylko informacje o sposobie używania [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] do zaimplementowania MVVM. Aby uzyskać więcej informacji na temat MVVM, zobacz [szybkiego startu MVVM](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).  
  
## <a name="classes-that-support-mvvm"></a>Klasy, które obsługują MVVM  
 Jeśli zostanie rozpoczęta [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, lub Windows Phone w wersji 7.5 dla Twojego [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, następujące klasy są dostępne w zakresie implementacji wzorca MVVM:  
  
-   <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>klasy  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>klasy  
  
-   <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>klasy  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>klasy  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>klasy  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>klasy  
  
-   <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>klasy  
  
-   <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>klasy  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>klasy  
  
-   <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>klasy  
  
-   Wszystkie klasy w <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> przestrzeni nazw  
  
## <a name="implementing-mvvm"></a>Implementowanie MVVM  
 Aby zaimplementować MVVM, zwykle tworzenia modelu i model widoku w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, ponieważ [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu nie może odwoływać się nieprzenośny projekt. Model i model widoku można w tym samym projekcie lub w oddzielnych projektów. Jeśli używasz osobne projekty, Dodaj odwołanie z widoku projektu modelu do projektu modelu.  
  
 Po skompilować model i przeglądać projekty modelu odwołują się te zestawy w aplikacji, która zawiera widok. Jeśli widok współpracuje tylko z modelu widoku, wystarczy odwoływać się do zestawu, który zawiera model widoku.  
  
### <a name="model"></a>Model  
 W poniższym przykładzie pokazano uproszczony model klasy, która może znajdować się w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 W poniższym przykładzie przedstawiono prosty sposób wypełniania, pobierania i aktualizowania danych w [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu. W rzeczywistym aplikacji może pobrać danych ze źródła, takie jak usługi Windows Communication Foundation (WCF).  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a>Model widoku  
 Podczas implementowania wzorzec MVVM często dodawany jest klasą bazową dla modeli widoku. W poniższym przykładzie przedstawiono klasę podstawową.  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 Implementacja interfejsu <xref:System.Windows.Input.ICommand> interfejs jest często używany ze wzorcem MVVM. Poniższy przykład przedstawia implementację <xref:System.Windows.Input.ICommand> interfejsu.  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 W poniższym przykładzie pokazano uproszczony widok modelu.  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Widok  
 Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikacji, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, oparte na technologii Silverlight aplikację lub aplikację systemu Windows Phone 7.5, możesz odwoływać się do zestawu, który zawiera projekty modelu modelu i widoku.  Następnie można utworzyć widoku, który współdziała z modelu widoku. W poniższym przykładzie pokazano uproszczony aplikacji Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku. Widoki podobnie można utworzyć w programie Silverlight, Windows Phone lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klas przenośnych](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
