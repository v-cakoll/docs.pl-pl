---
title: 'Przykład: rozwiązywanie problemów z programowaniem dynamicznym'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128441"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Przykład: rozwiązywanie problemów z programowaniem dynamicznym
> [!NOTE]
> Ten temat dotyczy wersji zapoznawczej programu .NET Native Developer, która jest oprogramowaniem w wersji wstępnej. Wersję zapoznawczą można pobrać z [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).  
  
 Nie wszystkie błędy wyszukiwania metadanych w aplikacjach utworzonych przy użyciu łańcucha narzędzi .NET Native powodują wystąpienie wyjątku.  Niektóre z nich mogą być manifestować w sposób nieprzewidywalny w aplikacji.  Poniższy przykład pokazuje naruszenie zasad dostępu spowodowany odwołaniem do obiektu o wartości null:  
  
```output
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
  
 Spróbujmy rozwiązać ten wyjątek, korzystając z podejścia z trzech kroków opisanych w sekcji "Ręczne rozwiązywanie brakujących metadanych" [wprowadzenie](getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Co to jest aplikacja?  
 Pierwszą rzeczą, którą należy zwrócić, jest `async` maszyn słowa kluczowego na podstawie stosu.  Określenie, co aplikacja była naprawdę wykonywana w metodzie `async` może być problematyczne, ponieważ stos utracił kontekst wywołania źródłowego i uruchomił kod `async` w innym wątku. Można jednak określić, że aplikacja próbuje załadować pierwszą stronę.  W implementacji dla `NavigationArgs.Setup`następujący kod spowodował naruszenie zasad dostępu:  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 W tym wystąpieniu Właściwość `LayoutVM` na `AppViewModel.Current` miała **wartość null**.  Niektóre z braku metadanych spowodowały delikatne różnice między zachowaniem i spowodowały niezainicjowanie właściwości zamiast ustawionej, ponieważ oczekiwano aplikacji.  Ustawienie punktu przerwania w kodzie, w którym `LayoutVM` powinna zostać zainicjowana, może spowodować wygenerowanie jasnej sytuacji.  Należy jednak pamiętać, że typ `LayoutVM`jest `App.Core.ViewModels.Layout.LayoutApplicationVM`.  Jedyną dyrektywą dotyczącą metadanych jest obecna w pliku Rd. XML:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Prawdopodobnie w `App.Core.ViewModels.Layout.LayoutApplicationVM` brakuje metadanych, ponieważ znajduje się ona w innej przestrzeni nazw.  
  
 W takim przypadku dodanie dyrektywy środowiska uruchomieniowego dla `App.Core.ViewModels` rozwiązało problem. Główną przyczyną było wywołanie interfejsu API metody <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType>, która zwróciła **wartość null**, a aplikacja dyskretnie zignorował problem do momentu wystąpienia awarii.  
  
 W programowaniu dynamicznym dobrym sposobem użycia interfejsów API odbicia w obszarze .NET Native jest użycie przeciążenia <xref:System.Type.GetType%2A?displayProperty=nameWithType>, które zgłaszają wyjątek w przypadku awarii.  
  
## <a name="is-this-an-isolated-case"></a>Czy to jest izolowany przypadek?  
 Inne problemy mogą również wystąpić w przypadku korzystania z `App.Core.ViewModels`.  Należy zdecydować, czy warto identyfikować i naprawiać każdy brakujący wyjątek metadanych lub zaoszczędzić czas i dodać dyrektywy dla większej klasy typów.  W tym miejscu, Dodawanie `dynamic` metadanych dla `App.Core.ViewModels` może być najlepszym rozwiązaniem, jeśli wynikowy wzrost rozmiaru danych binarnych nie jest problemem.  
  
## <a name="could-the-code-be-rewritten"></a>Czy kod można napisać ponownie?  
 Jeśli aplikacja używała `typeof(LayoutApplicationVM)` zamiast `Type.GetType("LayoutApplicationVM")`, łańcuch narzędzi mógłby zachować metadane `browse`.  Mimo to nadal nie utworzy `invoke` metadanych, co spowodowałoby wyjątek [MissingMetadataException](missingmetadataexception-class-net-native.md) podczas tworzenia wystąpienia typu. Aby zapobiec wyjątku, nadal trzeba dodać dyrektywę środowiska uruchomieniowego dla przestrzeni nazw lub typ, który określa zasady `dynamic`. Aby uzyskać informacje na temat dyrektyw środowiska uruchomieniowego, zobacz [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-with-net-native.md)
- [Przykład: Obsługa wyjątków podczas wiązania danych](example-handling-exceptions-when-binding-data.md)
