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
# <a name="using-portable-class-library-with-model-view-view-model"></a>Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model
Można użyć programu .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementacji wzorca Model-View-View Model (MVVM) i udostępnianie zestawów na wielu platformach.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM jest wzorzec aplikacji, który izoluje w interfejsie użytkownika z podstawowej logiki biznesowej. Można zaimplementować klasy modelu modelu i widoku w projekcie biblioteki klas przenośnych w programie Visual Studio 2012, a następnie Utwórz widoki, które są dostosowywane na różnych platformach. Dzięki temu można zapisać danych modelu i logikę biznesową tylko raz i użycia, ten kod z .NET Framework, Silverlight, Windows Phone i [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, jak pokazano na poniższej ilustracji.

 ![Pokazuje Portable Class Library za pomocą zestawów RMS sharing MVVM między platformami.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Ten temat nie zawiera ogólne informacje dotyczące wzorca MVVM. Tylko zawiera informacje o sposobie używania biblioteki klas przenośnych do zaimplementowania MVVM. Aby uzyskać więcej informacji na temat MVVM zobacz [MVVM Szybki Start za pomocą biblioteki Prism 5.0 biblioteki dla WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Klasy, które obsługują MVVM
 Gdy miejscem docelowym .NET Framework 4.5 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight lub Windows Phone 7.5 dla Twojego projektu Portable Class Library następujące klasy są dostępne do implementowania wzorca MVVM:

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Klasa

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Klasa

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Klasa

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Klasa

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Klasa

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Klasa

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Klasa

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Klasa

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Klasa

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Klasa

- Wszystkie klasy w <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> przestrzeni nazw

## <a name="implementing-mvvm"></a>Implementowanie MVVM
 Aby zaimplementować MVVM, zwykle tworzenia modelu i model widoku w projekcie biblioteki klas przenośnych, ponieważ projekt przenośnej biblioteki klas nie może odwoływać się do projektu nieprzenośne. Model i widoku modelu może być w tym samym projekcie lub w oddzielnych projektów. Użycie oddzielnych projektów, Dodaj odwołanie z projektu modelu widoku projektu modelu.

 Po skompilować model i wyświetlanie modelu projektów, możesz tych zestawów odwołań w aplikację, która zawiera widok. Jeśli widok współdziała tylko z modelu widoku, wystarczy odwołać się do zestawu, który zawiera model widoku.

### <a name="model"></a>Model
 Poniższy przykład przedstawia klasę uproszczony model, który może znajdować się w projekcie biblioteki klas przenośnych.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 Poniższy przykład pokazuje prosty sposób wypełnić, pobieranie i aktualizowanie danych w projekcie biblioteki klas przenośnych. W rzeczywistej aplikacji może pobrać dane ze źródła, takich jak usługi Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Model widoku
 Klasa bazowa dla modeli widoków często jest dodawany podczas implementowania wzorca MVVM. Poniższy przykład przedstawia klasę bazową.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Implementacja <xref:System.Windows.Input.ICommand> interfejsu jest często używany przy użyciu wzorca MVVM. W poniższym przykładzie pokazano implementację <xref:System.Windows.Input.ICommand> interfejsu.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 Poniższy przykład pokazuje wzór uproszczony widok.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Widok  
 Z poziomu aplikacji .NET Framework 4.5 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, aplikacji opartych na technologii Silverlight lub aplikacji Windows Phone 7.5 można odwoływać się zestaw, który zawiera projekty modelu i widoku modelu.  Następnie utworzysz widok, który wchodzi w interakcję z modelu widoku. Poniższy przykład przedstawia uproszczoną aplikację Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku. Można utworzyć podobne widoki w programie Silverlight, Windows Phone lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klas przenośnych](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
