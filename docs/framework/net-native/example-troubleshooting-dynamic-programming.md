---
title: 'Przykład: Rozwiązywanie problemów z programowaniem dynamicznym'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e482303e684813574a092f0a2d5812445ed7fa6e
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052615"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Przykład: Rozwiązywanie problemów z programowaniem dynamicznym
> [!NOTE]
>  W tym temacie odnosi się do platformy .NET Native Developer Preview, czyli wstępnej wersji oprogramowania. Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Nie wszystkie metadane wyszukiwania błędów w aplikacjach opracowanych za pomocą platformy .NET Native wynik łańcuch narzędzi w wyjątek.  Niektóre mogą manifestu w sposób nieprzewidziany w aplikacji.  Naruszenie zasad dostępu spowodowana przez utworzenie odwołań do obiektów o wartości null można znaleźć w poniższym przykładzie:  
  
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
  
 Wypróbujmy rozwiązywać problemy z tym wyjątkiem, przy użyciu podejścia trzech kroków opisanych w sekcji "Ręcznie rozwiązać Brak metadanych" [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Została aplikacja działania?  
 W pierwszej kolejności należy pamiętać, `async` maszyn — słowo kluczowe z podstawową stosu.  Określanie aplikacji była naprawdę działania `async` metoda może być problematyczne, ponieważ stos utracił Kontekst wywołania źródłowy i zostało uruchomione `async` kod w innym wątku. Jednak firma Microsoft wywnioskować, że aplikacja próbuje załadować jej pierwszej strony.  W implementacji dla `NavigationArgs.Setup`, poniższy kod spowodował naruszenie zasad dostępu:  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 W tym wypadku `LayoutVM` właściwość `AppViewModel.Current` został **null**.  Niektóre Brak metadanych spowodowała różnica zachowanie delikatny i spowodowało właściwość jest niezainicjowane zamiast zestawu, co aplikacja oczekuje.  Ustawienie punktu przerwania w kodzie gdzie `LayoutVM` należy zainicjować może zgłosić światło na sytuację.  Jednak należy pamiętać, że `LayoutVM`jego typ jest `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Do tej pory w pliku rd.xml dyrektywy tylko metadanych jest:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Prawdopodobnie Release candidate błędu jest to, że `App.Core.ViewModels.Layout.LayoutApplicationVM` Brak metadanych, ponieważ jest ona w innej przestrzeni nazw.  
  
 W tym przypadku Dodawanie dyrektyw środowiska uruchomieniowego, aby uzyskać `App.Core.ViewModels` rozwiązała problem. Główną przyczyną była do wywołań interfejsu API <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodę, która jest zwracana **null**, i aplikacja dyskretnie ignorowana problem do momentu awarii wystąpił.  
  
 W programowaniu dynamiczne, dobrym rozwiązaniem, gdy za pomocą odbicia interfejsów API w ramach platformy .NET Native jest użycie <xref:System.Type.GetType%2A?displayProperty=nameWithType> przeciążenia, które zgłoszenie wyjątku w przypadku niepowodzenia.  
  
## <a name="is-this-an-isolated-case"></a>Jest to przypadek w izolowanym?  
 Inne problemy z również mogą wystąpić w przypadku korzystania z `App.Core.ViewModels`.  Należy zdecydować, czy warto identyfikowanie i rozwiązywanie każdego wyjątku Brak metadanych lub oszczędzanie czasu i dodanie dyrektywy do większej klasy typów.  W tym miejscu, dodając `dynamic` metadanych dla `App.Core.ViewModels` może być najlepszym rozwiązaniem, jeśli powstałe zwiększenie rozmiaru wyjściowych danych binarnych nie będzie to problemem.  
  
## <a name="could-the-code-be-rewritten"></a>Można dopasować kod?  
 Jeśli aplikacja była wykorzystywana `typeof(LayoutApplicationVM)` zamiast `Type.GetType("LayoutApplicationVM")`, może mieć zachowane łańcucha narzędzi `browse` metadanych.  Jednak go jeszcze nie zostały utworzone `invoke` metadanych, które doprowadziłoby do [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek podczas tworzenia wystąpienia typu. Aby zapobiec wyjątku, nadal trzeba dodać dyrektyw środowiska uruchomieniowego w przestrzeni nazw lub typ, który określa `dynamic` zasad. Aby uzyskać informacje dotyczące dyrektywy środowiska uruchomieniowego, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Przykład: Obsługa wyjątków podczas powiązywania danych](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
