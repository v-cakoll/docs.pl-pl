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
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="8cc17-102">Przykład: Rozwiązywanie problemów z programowaniem dynamicznym</span><span class="sxs-lookup"><span data-stu-id="8cc17-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
> <span data-ttu-id="8cc17-103">Ten temat dotyczy wersji zapoznawczej programu .NET Native Developer, która jest oprogramowaniem w wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="8cc17-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="8cc17-104">Wersję zapoznawczą można pobrać z [witryny sieci Web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (wymaga rejestracji).</span><span class="sxs-lookup"><span data-stu-id="8cc17-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="8cc17-105">Nie wszystkie błędy wyszukiwania metadanych w aplikacjach utworzonych przy użyciu łańcucha narzędzi .NET Native powodują wystąpienie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8cc17-105">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="8cc17-106">Niektóre z nich mogą być manifestować w sposób nieprzewidywalny w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cc17-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="8cc17-107">Poniższy przykład pokazuje naruszenie zasad dostępu spowodowany odwołaniem do obiektu o wartości null:</span><span class="sxs-lookup"><span data-stu-id="8cc17-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="8cc17-108">Spróbujmy rozwiązać ten wyjątek, korzystając z podejścia z trzech kroków opisanych w sekcji "Ręczne rozwiązywanie brakujących metadanych" [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="8cc17-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="8cc17-109">Co to jest aplikacja?</span><span class="sxs-lookup"><span data-stu-id="8cc17-109">What was the app doing?</span></span>  
 <span data-ttu-id="8cc17-110">Pierwszą rzeczą, którą należy zwrócić, `async` jest maszyna słowa kluczowego na podstawie stosu.</span><span class="sxs-lookup"><span data-stu-id="8cc17-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="8cc17-111">Określenie, co aplikacja była naprawdę wykonywana w `async` metodzie, może być problematyczne, ponieważ stos utracił kontekst wywołania źródłowego i `async` uruchomił kod w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="8cc17-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="8cc17-112">Można jednak określić, że aplikacja próbuje załadować pierwszą stronę.</span><span class="sxs-lookup"><span data-stu-id="8cc17-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="8cc17-113">W implementacji dla `NavigationArgs.Setup`programu następujący kod spowodował naruszenie zasad dostępu:</span><span class="sxs-lookup"><span data-stu-id="8cc17-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="8cc17-114">W tym wystąpieniu `LayoutVM` `AppViewModel.Current` Właściwość **ma wartość null**.</span><span class="sxs-lookup"><span data-stu-id="8cc17-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="8cc17-115">Niektóre z braku metadanych spowodowały delikatne różnice między zachowaniem i spowodowały niezainicjowanie właściwości zamiast ustawionej, ponieważ oczekiwano aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cc17-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="8cc17-116">Ustawienie punktu przerwania w kodzie, `LayoutVM` w którym powinna zostać zainicjowana, może spowodować wygenerowanie jasnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="8cc17-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="8cc17-117">Należy jednak pamiętać, `LayoutVM`że jest to `App.Core.ViewModels.Layout.LayoutApplicationVM`typ.</span><span class="sxs-lookup"><span data-stu-id="8cc17-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="8cc17-118">Jedyną dyrektywą dotyczącą metadanych jest obecna w pliku Rd. XML:</span><span class="sxs-lookup"><span data-stu-id="8cc17-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="8cc17-119">Prawdopodobnie kandydat dla niepowodzenia to brak metadanych `App.Core.ViewModels.Layout.LayoutApplicationVM` , ponieważ znajduje się ona w innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cc17-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="8cc17-120">W takim przypadku dodanie dyrektywy środowiska uruchomieniowego w `App.Core.ViewModels` celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="8cc17-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="8cc17-121">Główna przyczyna to wywołanie <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> interfejsu API metody, która zwróciła **wartość null**, a aplikacja dyskretnie zignorował problem do momentu wystąpienia awarii.</span><span class="sxs-lookup"><span data-stu-id="8cc17-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="8cc17-122">W programowaniu dynamicznym dobrym sposobem korzystania z <xref:System.Type.GetType%2A?displayProperty=nameWithType> interfejsów API odbicia w obszarze .NET Native jest użycie przeciążeń, które generują wyjątek w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="8cc17-122">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="8cc17-123">Czy to jest izolowany przypadek?</span><span class="sxs-lookup"><span data-stu-id="8cc17-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="8cc17-124">Inne problemy mogą również wystąpić podczas korzystania `App.Core.ViewModels`z programu.</span><span class="sxs-lookup"><span data-stu-id="8cc17-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="8cc17-125">Należy zdecydować, czy warto identyfikować i naprawiać każdy brakujący wyjątek metadanych lub zaoszczędzić czas i dodać dyrektywy dla większej klasy typów.</span><span class="sxs-lookup"><span data-stu-id="8cc17-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="8cc17-126">W tym miejscu `dynamic` dodawanie metadanych `App.Core.ViewModels` dla programu może być najlepszym rozwiązaniem, jeśli wzrost rozmiaru danych binarnych wyjściowych nie jest problemem.</span><span class="sxs-lookup"><span data-stu-id="8cc17-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="8cc17-127">Czy kod można napisać ponownie?</span><span class="sxs-lookup"><span data-stu-id="8cc17-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="8cc17-128">Jeśli aplikacja była używana `typeof(LayoutApplicationVM)` `Type.GetType("LayoutApplicationVM")`zamiast, łańcuch narzędzi mógłby zachować `browse` metadane.</span><span class="sxs-lookup"><span data-stu-id="8cc17-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="8cc17-129">Mimo to nadal nie utworzy `invoke` metadanych, co spowodowałoby wyjątek [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="8cc17-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="8cc17-130">Aby zapobiec wyjątku, nadal trzeba dodać dyrektywę środowiska uruchomieniowego dla przestrzeni nazw lub typ, który określa `dynamic` zasady.</span><span class="sxs-lookup"><span data-stu-id="8cc17-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="8cc17-131">Aby uzyskać informacje na temat dyrektyw środowiska uruchomieniowego, zobacz [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (RD. xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8cc17-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc17-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cc17-132">See also</span></span>

- [<span data-ttu-id="8cc17-133">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8cc17-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="8cc17-134">Przykład: Obsługa wyjątków podczas wiązania danych</span><span class="sxs-lookup"><span data-stu-id="8cc17-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
