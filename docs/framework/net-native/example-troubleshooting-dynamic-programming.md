---
title: "Przykład: rozwiązywanie problemów z programowaniem dynamicznym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fdf3f12b325282b048420f57befa752f3f3f6803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="b88b5-102">Przykład: rozwiązywanie problemów z programowaniem dynamicznym</span><span class="sxs-lookup"><span data-stu-id="b88b5-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="b88b5-103">W tym temacie odnosi się do .NET Native Developer Preview, która jest wersja wstępna oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="b88b5-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="b88b5-104">Możesz pobrać podglądu [witryny sieci Web Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).</span><span class="sxs-lookup"><span data-stu-id="b88b5-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="b88b5-105">Nie wszystkie błędy wyszukiwania metadanych w aplikacji utworzonych przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia wyniku łańcuch wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b88b5-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="b88b5-106">Niektóre można manifestu w sposób nieprzewidziany w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b88b5-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="b88b5-107">W poniższym przykładzie przedstawiono naruszenia zasad dostępu spowodowane odwołujący się do obiektu null:</span><span class="sxs-lookup"><span data-stu-id="b88b5-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="b88b5-108">Spróbujmy rozwiązywać ten wyjątek przy użyciu podejścia trzech kroków opisanych w sekcji "Ręcznie rozwiązać Brak metadanych" [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="b88b5-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="b88b5-109">Co wykonywanych aplikacji?</span><span class="sxs-lookup"><span data-stu-id="b88b5-109">What was the app doing?</span></span>  
 <span data-ttu-id="b88b5-110">Najpierw należy pamiętać, jest `async` maszyny — słowo kluczowe na podstawie stosu.</span><span class="sxs-lookup"><span data-stu-id="b88b5-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="b88b5-111">Określanie, co aplikacja naprawdę wykonywanych `async` metoda może być powodować problemów, ponieważ stos utracił kontekstu wywołania pochodzące i zostało uruchomione `async` kodu w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="b88b5-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="b88b5-112">Jednak firma Microsoft wywnioskować, że aplikacja próbuje załadować swojej pierwszej strony.</span><span class="sxs-lookup"><span data-stu-id="b88b5-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="b88b5-113">W implementacji dla `NavigationArgs.Setup`, poniższy kod spowodował naruszenie zasad dostępu:</span><span class="sxs-lookup"><span data-stu-id="b88b5-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="b88b5-114">W tym wystąpieniu `LayoutVM` właściwość `AppViewModel.Current` został **null**.</span><span class="sxs-lookup"><span data-stu-id="b88b5-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="b88b5-115">Brak niektórych metadanych spowodował zachowanie niewielkie różnice, wynikiem jest niezainicjowana zamiast zestawu, co aplikacja Oczekiwano właściwości.</span><span class="sxs-lookup"><span data-stu-id="b88b5-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="b88b5-116">Ustawienia punktu przerwania w kodzie gdzie `LayoutVM` należy zainicjować może zgłosić światła w sytuacji.</span><span class="sxs-lookup"><span data-stu-id="b88b5-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="b88b5-117">Jednak należy pamiętać, że `LayoutVM`jego typ jest `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="b88b5-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="b88b5-118">Dyrektywa metadane tylko do tej pory w pliku rd.xml jest:</span><span class="sxs-lookup"><span data-stu-id="b88b5-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="b88b5-119">Prawdopodobnie candidate błędu jest to, że `App.Core.ViewModels.Layout.LayoutApplicationVM` Brak metadanych, ponieważ znajduje się w innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b88b5-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="b88b5-120">W takim przypadku dodanie dyrektywy środowiska uruchomieniowego dla `App.Core.ViewModels` rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="b88b5-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="b88b5-121">Główną przyczynę został wywołanie interfejsu API <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> metodę, która jest zwracana **null**, i aplikacja dyskretnie ignorowane problem do czasu podczas awarii.</span><span class="sxs-lookup"><span data-stu-id="b88b5-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="b88b5-122">W dynamicznie programowania, dobrym rozwiązaniem w przypadku korzystania z interfejsów API odbicia w obszarze [!INCLUDE[net_native](../../../includes/net-native-md.md)] jest użycie <xref:System.Type.GetType%2A?displayProperty=nameWithType> przeciążeń, które zgłosić wyjątek, w przypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="b88b5-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="b88b5-123">To jest izolowane przypadku?</span><span class="sxs-lookup"><span data-stu-id="b88b5-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="b88b5-124">Inne problemy mogą wystąpić także, korzystając z `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="b88b5-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="b88b5-125">Należy zdecydować, czy warto identyfikacji i rozwiązywania każdego Brak wyjątku metadanych lub oszczędzając czas i dodanie dyrektywy większych klasy typów.</span><span class="sxs-lookup"><span data-stu-id="b88b5-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="b88b5-126">W tym miejscu Dodawanie `dynamic` metadanych dla `App.Core.ViewModels` może być najlepszym rozwiązaniem, jeśli problem nie jest powstałe zwiększenie rozmiaru wynikowego pliku binarnego.</span><span class="sxs-lookup"><span data-stu-id="b88b5-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="b88b5-127">Może być ulegną kod?</span><span class="sxs-lookup"><span data-stu-id="b88b5-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="b88b5-128">Jeśli aplikacja była wykorzystywana `typeof(LayoutApplicationVM)` zamiast `Type.GetType("LayoutApplicationVM")`, może mieć zachowane łańcucha narzędzi `browse` metadanych.</span><span class="sxs-lookup"><span data-stu-id="b88b5-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="b88b5-129">Jednak go jeszcze nie utworzono `invoke` metadanych, które doprowadziłoby do [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątek podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="b88b5-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="b88b5-130">Aby zapobiec wyjątek, może nadal jest konieczne Dodaj dyrektywy środowiska uruchomieniowego dla przestrzeni nazw lub typ, który określa `dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="b88b5-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="b88b5-131">Aby uzyskać informacje na dyrektyw środowiska uruchomieniowego, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="b88b5-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88b5-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b88b5-132">See Also</span></span>  
 [<span data-ttu-id="b88b5-133">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="b88b5-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="b88b5-134">Przykład: Obsługa wyjątków podczas wiązania danych</span><span class="sxs-lookup"><span data-stu-id="b88b5-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
