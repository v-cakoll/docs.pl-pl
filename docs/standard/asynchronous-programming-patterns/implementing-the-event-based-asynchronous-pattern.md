---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
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
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 77156eb1ceeb549ce5fe09532e05096376b4569b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="2f930-102">Implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="2f930-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="2f930-103">Podczas pisania klasy z niektórych operacji, które może pociągnąć za sobą zauważalnego opóźnienia, należy wziąć pod uwagę nadanie mu funkcji asynchroniczności zaimplementowanie [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="2f930-104">Asynchroniczny wzorzec oparty na zdarzeniach umożliwia standardowych pakietu klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="2f930-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="2f930-105">Zaimplementowany przy użyciu Pomocnika klas takich jak <xref:System.ComponentModel.AsyncOperationManager>, klasy będzie działać poprawnie w dowolnej aplikacji modelu, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplikacje konsoli i aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2f930-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="2f930-106">Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="2f930-107">Proste operacje asynchroniczne, może znaleźć <xref:System.ComponentModel.BackgroundWorker> odpowiedniego składnika.</span><span class="sxs-lookup"><span data-stu-id="2f930-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="2f930-108">Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker>, zobacz [porady: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="2f930-109">Poniższa lista zawiera opis funkcji oparty na zdarzeniach wzorca asynchronicznego omówione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="2f930-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="2f930-110">Możliwości w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="2f930-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="2f930-111">Nazwy metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="2f930-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="2f930-112">Opcjonalnie obsługiwać anulowania</span><span class="sxs-lookup"><span data-stu-id="2f930-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="2f930-113">Opcjonalnie obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="2f930-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="2f930-114">Opcjonalnie zapewniają obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="2f930-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="2f930-115">Opcjonalnie zapewniają obsługę zwracania wyników przyrostowe</span><span class="sxs-lookup"><span data-stu-id="2f930-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="2f930-116">Obsługa Out i Ref parametrów metod</span><span class="sxs-lookup"><span data-stu-id="2f930-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="2f930-117">Możliwości w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="2f930-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="2f930-118">Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach po:</span><span class="sxs-lookup"><span data-stu-id="2f930-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="2f930-119">Nie ma potrzeby klientów klasy <xref:System.Threading.WaitHandle> i <xref:System.IAsyncResult> obiekty dostępne dla operacji asynchronicznych, co oznacza, że sondowania i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> musi być tworzone przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2f930-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="2f930-120">Chcesz, aby operacje asynchroniczne, które mają być zarządzane przez klienta z modelem znanych zdarzeń lub obiekt delegowany.</span><span class="sxs-lookup"><span data-stu-id="2f930-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="2f930-121">Żadnej operacji jest kandydatem do asynchronicznego implementacji, ale należy rozważyć te może pociągnąć za sobą długie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="2f930-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="2f930-122">Szczególnie przydatne są operacje, w których klienci wywołania metody i są powiadamiani o po zakończeniu, bez potrzeby interwencji dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="2f930-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="2f930-123">Odpowiednie są również działań, które w sposób ciągły, uruchom okresowo powiadamiania klientów postępu, przyrostowe wyników lub zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="2f930-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="2f930-124">Aby uzyskać więcej informacji o podjęcie decyzji o obsługującego wzorzec asynchroniczny oparty na zdarzeniach, zobacz [przy wyborze, gdy do implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="2f930-125">Nazwy metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="2f930-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="2f930-126">Dla każdej z metod synchronicznych *MethodName* dla którego chcesz podać asynchroniczne odpowiednikiem:</span><span class="sxs-lookup"><span data-stu-id="2f930-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="2f930-127">Zdefiniuj *MethodName* `Async` metody który:</span><span class="sxs-lookup"><span data-stu-id="2f930-127">Define a *MethodName*`Async` method that:</span></span>  
  
-   <span data-ttu-id="2f930-128">Zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="2f930-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="2f930-129">Trwa takich samych parametrach co *MethodName* metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="2f930-130">Akceptuje wiele wywołań.</span><span class="sxs-lookup"><span data-stu-id="2f930-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="2f930-131">Opcjonalnie zdefiniować *MethodName* `Async` przeciążenia taki sam jak *MethodName*`Async`, ale bez dodatkowy parametr zwracającej obiekt o nazwie `userState`.</span><span class="sxs-lookup"><span data-stu-id="2f930-131">Optionally define a *MethodName*`Async` overload, identical to *MethodName*`Async`, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="2f930-132">Jeśli jest przygotowane do zarządzania wielu współbieżnych wywołań metodę, w którym to przypadku `userState` wartości będą dostarczane do wszystkich procedur obsługi zdarzeń w celu odróżnienia wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="2f930-133">Można też to zrobić po prostu jako miejsce do przechowywania stanu użytkownika późniejszym pobierania.</span><span class="sxs-lookup"><span data-stu-id="2f930-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="2f930-134">Dla każdej szczegółowej *MethodName* `Async` podpis metody:</span><span class="sxs-lookup"><span data-stu-id="2f930-134">For each separate *MethodName*`Async` method signature:</span></span>  
  
1.  <span data-ttu-id="2f930-135">W tej samej klasie metodą, należy zdefiniować następujące zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="2f930-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="2f930-136">Zdefiniuj następujące delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2f930-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="2f930-137">Te będą prawdopodobnie zdefiniowania poza samej klasy, ale w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2f930-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   <span data-ttu-id="2f930-138">Upewnij się, że *MethodName* `CompletedEventArgs` klasy udostępnia jej elementów członkowskich jako właściwości tylko do odczytu i nie pola jako pola Zapobiegaj wiązania z danymi.</span><span class="sxs-lookup"><span data-stu-id="2f930-138">Ensure that the *MethodName*`CompletedEventArgs` class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="2f930-139">Nie definiują <xref:System.ComponentModel.AsyncCompletedEventArgs>-pochodnych klas do metody, które nie dostarczyło wyników.</span><span class="sxs-lookup"><span data-stu-id="2f930-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="2f930-140">Po prostu użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> samej siebie.</span><span class="sxs-lookup"><span data-stu-id="2f930-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f930-141">Doskonale dopuszczalne jest, gdy to możliwe i należy używać ponownie delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów.</span><span class="sxs-lookup"><span data-stu-id="2f930-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="2f930-142">W takim przypadku nazewnictwo nie będzie jako zgodne z nazwą metody od danego obiektu delegowanego i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie będą powiązane do pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="2f930-143">Opcjonalnie obsługiwać anulowania</span><span class="sxs-lookup"><span data-stu-id="2f930-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="2f930-144">Jeśli klasa będzie obsługiwał anulowanie operacji asynchronicznych, powinny zostać ujawnione anulowania do klienta, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="2f930-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="2f930-145">Należy pamiętać, że istnieją dwa punkty decyzyjne, które trzeba osiągnąć przed zdefiniowaniem zainteresowanie anulowania:</span><span class="sxs-lookup"><span data-stu-id="2f930-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="2f930-146">Klasy, w tym przyszłych przewidywanego dodatków, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?</span><span class="sxs-lookup"><span data-stu-id="2f930-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="2f930-147">Można operacje asynchroniczne, które obsługują wiele oczekujących operacji anulowania obsługi?</span><span class="sxs-lookup"><span data-stu-id="2f930-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="2f930-148">Oznacza to, że jest *MethodName* `Async` Wykonaj metodę `userState` parametru i jest możliwe wielu wywołań przed oczekiwania na zakończenie?</span><span class="sxs-lookup"><span data-stu-id="2f930-148">That is, does the *MethodName*`Async` method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="2f930-149">Użyj odpowiedzi na te pytania dwóch w poniższej tabeli, aby określić, jakie powinny być sygnatury dla metody anulowania.</span><span class="sxs-lookup"><span data-stu-id="2f930-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="2f930-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f930-150">Visual Basic</span></span>  
  
||<span data-ttu-id="2f930-151">Wiele równoczesnych operacji obsługiwane</span><span class="sxs-lookup"><span data-stu-id="2f930-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="2f930-152">Tylko jedną operację naraz</span><span class="sxs-lookup"><span data-stu-id="2f930-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="2f930-153">Jednej operacji asynchronicznej w całej klasy</span><span class="sxs-lookup"><span data-stu-id="2f930-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="2f930-154">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="2f930-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="2f930-155">C#</span><span class="sxs-lookup"><span data-stu-id="2f930-155">C#</span></span>  
  
||<span data-ttu-id="2f930-156">Wiele równoczesnych operacji obsługiwane</span><span class="sxs-lookup"><span data-stu-id="2f930-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="2f930-157">Tylko jedną operację naraz</span><span class="sxs-lookup"><span data-stu-id="2f930-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="2f930-158">Jednej operacji asynchronicznej w całej klasy</span><span class="sxs-lookup"><span data-stu-id="2f930-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="2f930-159">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="2f930-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="2f930-160">W przypadku definiowania `CancelAsync(object userState)` metody klientów należy zachować ostrożność, wybierając wartości stanu, aby pozwala na rozróżniania wśród wszystkich metod asynchronicznych wywołana dla obiektu, a nie tylko od wszystkich wywołań jednej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="2f930-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="2f930-161">Decyzja o nazwę wersji jednym asynchroniczne operacje *MethodName* `AsyncCancel` opiera się na było łatwiej odnaleźć metody w środowisku projektowania, takie jak IntelliSense programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f930-161">The decision to name the single-async-operation version *MethodName*`AsyncCancel` is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="2f930-162">Grupuje pokrewne elementy członkowskie, a odróżnia je od innych elementów członkowskich, które nie mają nic wspólnego z funkcji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="2f930-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="2f930-163">Jeśli przypuszczasz, że mogą istnieć dodatkowe operacje asynchroniczne dodane w kolejnych wersjach, lepiej zdefiniować `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="2f930-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="2f930-164">Wiele metod z powyższej tabeli nie zostaną zdefiniowane w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="2f930-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="2f930-165">Że nie ma sensu lub będzie zajmowały interfejsu klasy z mnożenie metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="2f930-166">Te metody zwykle zwróci natychmiast i operacji może lub nie może faktycznie anulowania.</span><span class="sxs-lookup"><span data-stu-id="2f930-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="2f930-167">W obsłudze zdarzeń dla *MethodName* `Completed` zdarzeń, *MethodName* `CompletedEventArgs` obiekt zawiera `Cancelled` pola, którego klienci mogą używać, aby określić, czy podczas anulowania.</span><span class="sxs-lookup"><span data-stu-id="2f930-167">In the event handler for the *MethodName*`Completed` event, the *MethodName*`CompletedEventArgs` object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="2f930-168">Przestrzegać semantyki anulowania opisanego w [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="2f930-169">Opcjonalnie obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="2f930-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="2f930-170">Jeśli klasa nie obsługuje wiele równoczesnych wywołań, należy wziąć pod uwagę udostępnianie `IsBusy` właściwości.</span><span class="sxs-lookup"><span data-stu-id="2f930-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="2f930-171">Dzięki temu deweloperzy mogą określić, czy *MethodName* `Async` metody działa bez przechwytywanie wyjątku z *MethodName* `Async` metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-171">This allows developers to determine whether a *MethodName*`Async` method is running without catching an exception from the *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="2f930-172">Przestrzegać `IsBusy` semantyki opisanego w [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="2f930-173">Opcjonalnie zapewniają obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="2f930-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="2f930-174">Jest często pożądane asynchronicznej operacji postępu raportu podczas jego działania.</span><span class="sxs-lookup"><span data-stu-id="2f930-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="2f930-175">Asynchroniczny wzorzec oparty na zdarzeniach zawiera wytyczne w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="2f930-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="2f930-176">Opcjonalnie zdefiniować zdarzenia wygenerowane przez operację asynchroniczną i wywołany w wątku odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="2f930-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="2f930-177"><xref:System.ComponentModel.ProgressChangedEventArgs> Obiektu prowadzi wskaźnik postępu wyliczaną, który może należeć do zakresu od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="2f930-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="2f930-178">Nazwa tego zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2f930-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="2f930-179">`ProgressChanged`Jeśli klasa ma wiele operacji asynchronicznych (lub jest oczekiwana Powiększ, aby dołączyć wielu operacji asynchronicznych w przyszłych wersjach);</span><span class="sxs-lookup"><span data-stu-id="2f930-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="2f930-180">*MethodName* `ProgressChanged` Jeśli klasa ma jednej operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="2f930-180">*MethodName* `ProgressChanged` if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="2f930-181">Ten wybór nazewnictwa równoleżnikami zgłaszającego dla metody anulowania, zgodnie z opisem w sekcji opcjonalnie anulowania obsługi.</span><span class="sxs-lookup"><span data-stu-id="2f930-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="2f930-182">To zdarzenie należy używać <xref:System.ComponentModel.ProgressChangedEventHandler> podpisu delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="2f930-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="2f930-183">Alternatywnie, jeśli wskaźnik postępu bardziej specyficznego dla domeny można podać (w przypadku wystąpienia odczytanych bajtów i łączna liczba bajtów dla operacji pobierania), następnie należy zdefiniować klasy pochodnej z <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2f930-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="2f930-184">Należy pamiętać, że istnieje tylko jeden `ProgressChanged` lub *MethodName* `ProgressChanged` zdarzenia dla klasy, niezależnie od liczby obsługiwanych metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="2f930-184">Note that there is only one `ProgressChanged` or *MethodName*`ProgressChanged` event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="2f930-185">Klienci powinni używać `userState` obiekt, który jest przekazywany do *MethodName* `Async` metody do odróżnienia postępu aktualizacji na wiele równoczesnych operacji.</span><span class="sxs-lookup"><span data-stu-id="2f930-185">Clients are expected to use the `userState` object that is passed to the *MethodName*`Async` methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="2f930-186">Mogą wystąpić sytuacje, w których wiele operacji obsługuje postępu i zwraca każdego innego wskaźnika postępu.</span><span class="sxs-lookup"><span data-stu-id="2f930-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="2f930-187">W tym przypadku jednej `ProgressChanged` zdarzeń nie jest odpowiedni i można rozważyć obsługi wielu `ProgressChanged` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2f930-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="2f930-188">W takim przypadku należy użyć wzorzec nazewnictwa *MethodName* `ProgressChanged` dla każdego *MethodName* `Async` metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-188">In this case use a naming pattern of *MethodName*`ProgressChanged` for each *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="2f930-189">Przestrzegać semantykę raportowania postępu opisane [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="2f930-190">Opcjonalnie zapewniają obsługę zwracania wyników przyrostowe</span><span class="sxs-lookup"><span data-stu-id="2f930-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="2f930-191">Czasami operację asynchroniczną może zwrócić wyniki przyrostowe przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="2f930-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="2f930-192">Istnieją różne opcje, które mogą służyć do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="2f930-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="2f930-193">Oto niektóre przykłady.</span><span class="sxs-lookup"><span data-stu-id="2f930-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="2f930-194">Klasy pojedynczej operacji</span><span class="sxs-lookup"><span data-stu-id="2f930-194">Single-operation Class</span></span>  
 <span data-ttu-id="2f930-195">Jeśli klasa obsługuje tylko jednej operacji asynchronicznych i tej operacji może zwrócić wyniki przyrostowych, następnie:</span><span class="sxs-lookup"><span data-stu-id="2f930-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="2f930-196">Rozszerzanie <xref:System.ComponentModel.ProgressChangedEventArgs> typu przenoszenia danych przyrostowych wyników i zdefiniuj *MethodName* `ProgressChanged` zdarzenie z rozszerzenia danych.</span><span class="sxs-lookup"><span data-stu-id="2f930-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName*`ProgressChanged` event with this extended data.</span></span>  
  
-   <span data-ttu-id="2f930-197">Zgłoś to *MethodName* `ProgressChanged` zdarzenie, gdy istnieje przyrostowe wynik do raportu.</span><span class="sxs-lookup"><span data-stu-id="2f930-197">Raise this *MethodName*`ProgressChanged` event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="2f930-198">To rozwiązanie dotyczy w szczególności klasy pojedynczej asynchronicznej operacji ponieważ nie ma problemów z tego samego zdarzenia występujące zwraca wyniki przyrostowe na "wszystkie operacje", jako *MethodName* `ProgressChanged` jest zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="2f930-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName*`ProgressChanged` event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="2f930-199">Klasa wielu operacji jednorodnych wyniki przyrostowe</span><span class="sxs-lookup"><span data-stu-id="2f930-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="2f930-200">W takim przypadku klasa obsługuje wiele metod asynchronicznych, każdy może zwracania wyników przyrostowych i przyrostowych wszystkie wyniki mają ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="2f930-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="2f930-201">Postępuj zgodnie z modelem opisane powyżej, aby klasy pojedynczej operacji, jako takie same <xref:System.EventArgs> struktury będzie działać w przypadku wszystkich wyników przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="2f930-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="2f930-202">Zdefiniuj `ProgressChanged` zdarzeń zamiast *MethodName* `ProgressChanged` zdarzenie, ponieważ dotyczy on wiele metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="2f930-202">Define a `ProgressChanged` event instead of a *MethodName*`ProgressChanged` event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="2f930-203">Klasa wielu operacji heterogenicznych wyniki przyrostowe</span><span class="sxs-lookup"><span data-stu-id="2f930-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="2f930-204">Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwracanie różnych typów danych, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2f930-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="2f930-205">Oddzielne przyrostowe wyników raportowania raportowania postępu.</span><span class="sxs-lookup"><span data-stu-id="2f930-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="2f930-206">Zdefiniuj oddzielnej *MethodName* `ProgressChanged` zdarzeń z odpowiednich <xref:System.EventArgs> dla każdej metody asynchronicznej do obsługi danych przyrostowych wyniku tej metody.</span><span class="sxs-lookup"><span data-stu-id="2f930-206">Define a separate *MethodName*`ProgressChanged` event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="2f930-207">Wywołania programu obsługi zdarzeń w odpowiednich wątku, zgodnie z opisem w [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2f930-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="2f930-208">Obsługa Out i Ref parametrów metod</span><span class="sxs-lookup"><span data-stu-id="2f930-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="2f930-209">Mimo że korzystanie z `out` i `ref` , ogólnie rzecz biorąc, zalecane w programie .NET Framework, poniżej przedstawiono zasady, zgodnie z którą są obecne:</span><span class="sxs-lookup"><span data-stu-id="2f930-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="2f930-210">Podana metoda synchroniczna *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="2f930-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="2f930-211">`out`Parametry *MethodName* nie powinna być częścią *MethodName*`Async`.</span><span class="sxs-lookup"><span data-stu-id="2f930-211">`out` parameters to *MethodName* should not be part of *MethodName*`Async`.</span></span> <span data-ttu-id="2f930-212">Zamiast tego powinna być częścią *MethodName* `CompletedEventArgs` o takiej samej nazwie jak jej parametr odpowiadającej *MethodName* (chyba że jest bardziej odpowiednia nazwa).</span><span class="sxs-lookup"><span data-stu-id="2f930-212">Instead, they should be part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="2f930-213">`ref`Parametry *MethodName* powinny się wyświetlać jako część *MethodName*`Async`i w ramach *MethodName* `CompletedEventArgs` o takiej samej nazwie jak jego Parametr odpowiadającej *MethodName* (chyba że jest bardziej odpowiednia nazwa).</span><span class="sxs-lookup"><span data-stu-id="2f930-213">`ref` parameters to *MethodName* should appear as part of *MethodName*`Async`, and as part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="2f930-214">Przykładowo podana:</span><span class="sxs-lookup"><span data-stu-id="2f930-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="2f930-215">Metodę asynchroniczną i jego <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2f930-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f930-216">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f930-216">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="2f930-217">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="2f930-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="2f930-218">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="2f930-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="2f930-219">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="2f930-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="2f930-220">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="2f930-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="2f930-221">Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="2f930-221">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="2f930-222">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="2f930-222">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
