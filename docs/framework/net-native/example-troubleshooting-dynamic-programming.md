---
title: 'Przykład: Rozwiązywanie problemów z programowaniem dynamicznym'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85d64a5577acdaa15a40ae308eb728d75d6a4c69
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894489"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Przykład: Rozwiązywanie problemów z programowaniem dynamicznym
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
  
 Spróbujmy rozwiązać ten wyjątek, korzystając z podejścia z trzech kroków opisanych w sekcji "Ręczne rozwiązywanie brakujących metadanych" [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Co to jest aplikacja?  
 Pierwszą rzeczą, którą należy zwrócić, `async` jest maszyna słowa kluczowego na podstawie stosu.  Określenie, co aplikacja była naprawdę wykonywana w `async` metodzie, może być problematyczne, ponieważ stos utracił kontekst wywołania źródłowego i `async` uruchomił kod w innym wątku. Można jednak określić, że aplikacja próbuje załadować pierwszą stronę.  W implementacji dla `NavigationArgs.Setup`programu następujący kod spowodował naruszenie zasad dostępu:  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 W tym wystąpieniu `LayoutVM` `AppViewModel.Current` Właściwość **ma wartość null**.  Niektóre z braku metadanych spowodowały delikatne różnice między zachowaniem i spowodowały niezainicjowanie właściwości zamiast ustawionej, ponieważ oczekiwano aplikacji.  Ustawienie punktu przerwania w kodzie, `LayoutVM` w którym powinna zostać zainicjowana, może spowodować wygenerowanie jasnej sytuacji.  Należy jednak pamiętać, `LayoutVM`że jest to `App.Core.ViewModels.Layout.LayoutApplicationVM`typ.  Jedyną dyrektywą dotyczącą metadanych jest obecna w pliku Rd. XML:  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 Prawdopodobnie kandydat dla niepowodzenia to brak metadanych `App.Core.ViewModels.Layout.LayoutApplicationVM` , ponieważ znajduje się ona w innej przestrzeni nazw.  
  
 W takim przypadku dodanie dyrektywy środowiska uruchomieniowego w `App.Core.ViewModels` celu rozwiązania problemu. Główna przyczyna to wywołanie <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> interfejsu API metody, która zwróciła **wartość null**, a aplikacja dyskretnie zignorował problem do momentu wystąpienia awarii.  
  
 W programowaniu dynamicznym dobrym sposobem korzystania z <xref:System.Type.GetType%2A?displayProperty=nameWithType> interfejsów API odbicia w obszarze .NET Native jest użycie przeciążeń, które generują wyjątek w przypadku niepowodzenia.  
  
## <a name="is-this-an-isolated-case"></a>Czy to jest izolowany przypadek?  
 Inne problemy mogą również wystąpić podczas korzystania `App.Core.ViewModels`z programu.  Należy zdecydować, czy warto identyfikować i naprawiać każdy brakujący wyjątek metadanych lub zaoszczędzić czas i dodać dyrektywy dla większej klasy typów.  W tym miejscu `dynamic` dodawanie metadanych `App.Core.ViewModels` dla programu może być najlepszym rozwiązaniem, jeśli wzrost rozmiaru danych binarnych wyjściowych nie jest problemem.  
  
## <a name="could-the-code-be-rewritten"></a>Czy kod można napisać ponownie?  
 Jeśli aplikacja była używana `typeof(LayoutApplicationVM)` `Type.GetType("LayoutApplicationVM")`zamiast, łańcuch narzędzi mógłby zachować `browse` metadane.  Mimo to nadal nie utworzy `invoke` metadanych, co spowodowałoby wyjątek [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) podczas tworzenia wystąpienia typu. Aby zapobiec wyjątku, nadal trzeba dodać dyrektywę środowiska uruchomieniowego dla przestrzeni nazw lub typ, który określa `dynamic` zasady. Aby uzyskać informacje na temat dyrektyw środowiska uruchomieniowego, zobacz [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (RD. xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Przykład: Obsługa wyjątków podczas wiązania danych](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
