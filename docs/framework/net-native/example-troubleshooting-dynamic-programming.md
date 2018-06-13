---
title: 'Przykład: rozwiązywanie problemów z programowaniem dynamicznym'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5de4388f4d3c4117ed71abd9741d2616638038d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397510"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Przykład: rozwiązywanie problemów z programowaniem dynamicznym
> [!NOTE]
>  W tym temacie odnosi się do .NET Native Developer Preview, która jest wersja wstępna oprogramowania. Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Nie wszystkie błędy wyszukiwania metadanych w aplikacji utworzonych przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia wyniku łańcuch wyjątku.  Niektóre można manifestu w sposób nieprzewidziany w aplikacji.  W poniższym przykładzie przedstawiono naruszenia zasad dostępu spowodowane odwołujący się do obiektu null:  
  
```  
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 Spróbujmy rozwiązywać ten wyjątek przy użyciu podejścia trzech kroków opisanych w sekcji "Ręcznie rozwiązać Brak metadanych" [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Co wykonywanych aplikacji?  
 Najpierw należy pamiętać, jest `async` maszyny — słowo kluczowe na podstawie stosu.  Określanie, co aplikacja naprawdę wykonywanych `async` metoda może być powodować problemów, ponieważ stos utracił kontekstu wywołania pochodzące i zostało uruchomione `async` kodu w innym wątku. Jednak firma Microsoft wywnioskować, że aplikacja próbuje załadować swojej pierwszej strony.  W implementacji dla `NavigationArgs.Setup`, poniższy kod spowodował naruszenie zasad dostępu:  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 W tym wystąpieniu `LayoutVM` właściwość `AppViewModel.Current` został **null**.  Brak niektórych metadanych spowodował zachowanie niewielkie różnice, wynikiem jest niezainicjowana zamiast zestawu, co aplikacja Oczekiwano właściwości.  Ustawienia punktu przerwania w kodzie gdzie `LayoutVM` należy zainicjować może zgłosić światła w sytuacji.  Jednak należy pamiętać, że `LayoutVM`jego typ jest `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Dyrektywa metadane tylko do tej pory w pliku rd.xml jest:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Prawdopodobnie candidate błędu jest to, że `App.Core.ViewModels.Layout.LayoutApplicationVM` Brak metadanych, ponieważ znajduje się w innej przestrzeni nazw.  
  
 W takim przypadku dodanie dyrektywy środowiska uruchomieniowego dla `App.Core.ViewModels` rozwiązać problem. Główną przyczynę został wywołanie interfejsu API <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodę, która jest zwracana **null**, i aplikacja dyskretnie ignorowane problem do czasu podczas awarii.  
  
 W dynamicznie programowania, dobrym rozwiązaniem w przypadku korzystania z interfejsów API odbicia w obszarze [!INCLUDE[net_native](../../../includes/net-native-md.md)] jest użycie <xref:System.Type.GetType%2A?displayProperty=nameWithType> przeciążeń, które zgłosić wyjątek, w przypadku awarii.  
  
## <a name="is-this-an-isolated-case"></a>To jest izolowane przypadku?  
 Inne problemy mogą wystąpić także, korzystając z `App.Core.ViewModels`.  Należy zdecydować, czy warto identyfikacji i rozwiązywania każdego Brak wyjątku metadanych lub oszczędzając czas i dodanie dyrektywy większych klasy typów.  W tym miejscu Dodawanie `dynamic` metadanych dla `App.Core.ViewModels` może być najlepszym rozwiązaniem, jeśli problem nie jest powstałe zwiększenie rozmiaru wynikowego pliku binarnego.  
  
## <a name="could-the-code-be-rewritten"></a>Może być ulegną kod?  
 Jeśli aplikacja była wykorzystywana `typeof(LayoutApplicationVM)` zamiast `Type.GetType("LayoutApplicationVM")`, może mieć zachowane łańcucha narzędzi `browse` metadanych.  Jednak go jeszcze nie utworzono `invoke` metadanych, które doprowadziłoby do [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek podczas tworzenia wystąpienia typu. Aby zapobiec wyjątek, może nadal jest konieczne Dodaj dyrektywy środowiska uruchomieniowego dla przestrzeni nazw lub typ, który określa `dynamic` zasad. Aby uzyskać informacje na dyrektyw środowiska uruchomieniowego, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Przykład: Obsługa wyjątków podczas wiązania danych](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
