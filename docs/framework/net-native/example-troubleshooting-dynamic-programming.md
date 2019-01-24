---
title: 'Przykład: Rozwiązywanie problemów z programowaniem dynamicznym'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53f17552a98683e4278dbdfbfa927ca3b075b225
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492289"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="d0e70-102">Przykład: Rozwiązywanie problemów z programowaniem dynamicznym</span><span class="sxs-lookup"><span data-stu-id="d0e70-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="d0e70-103">W tym temacie odnosi się do platformy .NET Native Developer Preview, czyli wstępnej wersji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="d0e70-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="d0e70-104">Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).</span><span class="sxs-lookup"><span data-stu-id="d0e70-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="d0e70-105">Nie wszystkie metadane wyszukiwania błędów w aplikacjach opracowanych za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia wynik łańcuch wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d0e70-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="d0e70-106">Niektóre mogą manifestu w sposób nieprzewidziany w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0e70-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="d0e70-107">Naruszenie zasad dostępu spowodowana przez utworzenie odwołań do obiektów o wartości null można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d0e70-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="d0e70-108">Wypróbujmy rozwiązywać problemy z tym wyjątkiem, przy użyciu podejścia trzech kroków opisanych w sekcji "Ręcznie rozwiązać Brak metadanych" [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="d0e70-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="d0e70-109">Została aplikacja działania?</span><span class="sxs-lookup"><span data-stu-id="d0e70-109">What was the app doing?</span></span>  
 <span data-ttu-id="d0e70-110">W pierwszej kolejności należy pamiętać, `async` maszyn — słowo kluczowe z podstawową stosu.</span><span class="sxs-lookup"><span data-stu-id="d0e70-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="d0e70-111">Określanie aplikacji była naprawdę działania `async` metoda może być problematyczne, ponieważ stos utracił Kontekst wywołania źródłowy i zostało uruchomione `async` kod w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="d0e70-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="d0e70-112">Jednak firma Microsoft wywnioskować, że aplikacja próbuje załadować jej pierwszej strony.</span><span class="sxs-lookup"><span data-stu-id="d0e70-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="d0e70-113">W implementacji dla `NavigationArgs.Setup`, poniższy kod spowodował naruszenie zasad dostępu:</span><span class="sxs-lookup"><span data-stu-id="d0e70-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="d0e70-114">W tym wypadku `LayoutVM` właściwość `AppViewModel.Current` został **null**.</span><span class="sxs-lookup"><span data-stu-id="d0e70-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="d0e70-115">Niektóre Brak metadanych spowodowała różnica zachowanie delikatny i spowodowało właściwość jest niezainicjowane zamiast zestawu, co aplikacja oczekuje.</span><span class="sxs-lookup"><span data-stu-id="d0e70-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="d0e70-116">Ustawienie punktu przerwania w kodzie gdzie `LayoutVM` należy zainicjować może zgłosić światło na sytuację.</span><span class="sxs-lookup"><span data-stu-id="d0e70-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="d0e70-117">Jednak należy pamiętać, że `LayoutVM`jego typ jest `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="d0e70-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="d0e70-118">Do tej pory w pliku rd.xml dyrektywy tylko metadanych jest:</span><span class="sxs-lookup"><span data-stu-id="d0e70-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="d0e70-119">Prawdopodobnie Release candidate błędu jest to, że `App.Core.ViewModels.Layout.LayoutApplicationVM` Brak metadanych, ponieważ jest ona w innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d0e70-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="d0e70-120">W tym przypadku Dodawanie dyrektyw środowiska uruchomieniowego, aby uzyskać `App.Core.ViewModels` rozwiązała problem.</span><span class="sxs-lookup"><span data-stu-id="d0e70-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="d0e70-121">Główną przyczyną była do wywołań interfejsu API <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodę, która jest zwracana **null**, i aplikacja dyskretnie ignorowana problem do momentu awarii wystąpił.</span><span class="sxs-lookup"><span data-stu-id="d0e70-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="d0e70-122">W dynamiczne programowanie, dobrym rozwiązaniem, gdy za pomocą interfejsów API odbicia w obszarze [!INCLUDE[net_native](../../../includes/net-native-md.md)] jest użycie <xref:System.Type.GetType%2A?displayProperty=nameWithType> przeciążenia, które zgłoszenie wyjątku w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="d0e70-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="d0e70-123">Jest to przypadek w izolowanym?</span><span class="sxs-lookup"><span data-stu-id="d0e70-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="d0e70-124">Inne problemy z również mogą wystąpić w przypadku korzystania z `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="d0e70-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="d0e70-125">Należy zdecydować, czy warto identyfikowanie i rozwiązywanie każdego wyjątku Brak metadanych lub oszczędzanie czasu i dodanie dyrektywy do większej klasy typów.</span><span class="sxs-lookup"><span data-stu-id="d0e70-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="d0e70-126">W tym miejscu, dodając `dynamic` metadanych dla `App.Core.ViewModels` może być najlepszym rozwiązaniem, jeśli powstałe zwiększenie rozmiaru wyjściowych danych binarnych nie będzie to problemem.</span><span class="sxs-lookup"><span data-stu-id="d0e70-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="d0e70-127">Można dopasować kod?</span><span class="sxs-lookup"><span data-stu-id="d0e70-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="d0e70-128">Jeśli aplikacja była wykorzystywana `typeof(LayoutApplicationVM)` zamiast `Type.GetType("LayoutApplicationVM")`, może mieć zachowane łańcucha narzędzi `browse` metadanych.</span><span class="sxs-lookup"><span data-stu-id="d0e70-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="d0e70-129">Jednak go jeszcze nie zostały utworzone `invoke` metadanych, które doprowadziłoby do [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="d0e70-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="d0e70-130">Aby zapobiec wyjątku, nadal trzeba dodać dyrektyw środowiska uruchomieniowego w przestrzeni nazw lub typ, który określa `dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="d0e70-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="d0e70-131">Aby uzyskać informacje dotyczące dyrektywy środowiska uruchomieniowego, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="d0e70-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e70-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0e70-132">See also</span></span>
- [<span data-ttu-id="d0e70-133">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="d0e70-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="d0e70-134">Przykład: Obsługa wyjątków podczas powiązywania danych</span><span class="sxs-lookup"><span data-stu-id="d0e70-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
