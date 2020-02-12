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
# <a name="using-portable-class-library-with-model-view-view-model"></a>Korzystanie z przenośnej biblioteki klas w połączeniu z modelem Model-View-View Model
Za pomocą [przenośnej biblioteki klas](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) .NET Framework można zaimplementować wzorzec Model-View-View Model (MVVM) i udostępnić zestawy na wielu platformach.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM jest wzorcem aplikacji, który izoluje interfejs użytkownika od podstawowej logiki biznesowej. Można wdrożyć model i wyświetlić klasy modelu w projekcie biblioteki klas przenośnych w programie Visual Studio 2012, a następnie utworzyć widoki, które są dostosowane dla różnych platform. Takie podejście umożliwia zapisanie modelu danych i logiki biznesowej tylko raz i użycie tego kodu z .NET Framework, Silverlight, Windows Phone i Windows 8. x aplikacji ze sklepu, jak pokazano na poniższej ilustracji.

 ![Pokazuje przenośną bibliotekę klas z zestawami udostępniania MVVM na różnych platformach.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Ten temat nie zawiera ogólnych informacji o wzorcu MVVM. Zawiera on tylko informacje o sposobach używania przenośnej biblioteki klas do implementowania MVVM. Aby uzyskać więcej informacji na temat MVVM, zobacz [Przewodnik Szybki Start MVVM przy użyciu biblioteki biblioteki Prism Library 5,0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Klasy obsługujące MVVM
 Jeśli obiektem docelowym jest .NET Framework 4,5, .NET dla aplikacji do sklepu Windows 8. x, Silverlight lub Windows Phone 7,5 dla projektu biblioteki klas przenośnych, do wdrożenia wzorca MVVM są dostępne następujące klasy:

- Klasa <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>

- Klasa <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>

- Klasa <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>

- Klasa <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>

- Klasa <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>

- Klasa <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>

- Klasa <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>

- Klasa <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>

- Klasa <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>

- Klasa <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>

- Wszystkie klasy w przestrzeni nazw <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>

## <a name="implementing-mvvm"></a>Implementowanie MVVM
 Aby zaimplementować MVVM, zazwyczaj tworzysz model i model widoku w projekcie biblioteki klas przenośnych, ponieważ projekt biblioteki klas przenośnych nie może odwoływać się do projektu nieprzenośnego. Model i model widoku mogą znajdować się w tym samym projekcie lub w oddzielnych projektach. Jeśli używasz oddzielnych projektów, Dodaj odwołanie z projektu modelu widoku do projektu modelu.

 Po skompilowaniu modelu i wyświetleniu projektów modelu należy odwołać się do tych zestawów w aplikacji, która zawiera widok. Jeśli widok współdziała tylko z modelem widoku, trzeba tylko odwołać się do zestawu, który zawiera model widoku.

### <a name="model"></a>Modelowanie
 W poniższym przykładzie przedstawiono uproszczoną klasę modelu, która może znajdować się w projekcie biblioteki klas przenośnych.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 Poniższy przykład pokazuje prostą metodę wypełniania, pobierania i aktualizowania danych w projekcie biblioteki klas przenośnych. W rzeczywistej aplikacji można pobrać dane ze źródła, takiego jak usługa Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Wyświetl model
 Klasa bazowa dla modeli widoków jest często dodawana podczas implementowania wzorca MVVM. Poniższy przykład pokazuje klasę bazową.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Implementacja interfejsu <xref:System.Windows.Input.ICommand> jest często używana ze wzorcem MVVM. W poniższym przykładzie przedstawiono implementację interfejsu <xref:System.Windows.Input.ICommand>.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 W poniższym przykładzie przedstawiono uproszczony model widoku.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Widok  
 Z poziomu aplikacji .NET Framework 4,5, aplikacji do sklepu Windows 8. x, aplikacji opartej na technologii Silverlight lub Windows Phone 7,5 aplikacji można odwołać się do zestawu, który zawiera model i widok projektów modelu.  Następnie utworzysz widok, który współdziała z modelem widoku. Poniższy przykład przedstawia uproszczoną aplikację Windows Presentation Foundation (WPF), która pobiera i aktualizuje dane z modelu widoku. Możesz tworzyć podobne widoki w aplikacjach w sklepie Silverlight, Windows Phone lub Windows 8. x.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Biblioteka klas przenośnych](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
