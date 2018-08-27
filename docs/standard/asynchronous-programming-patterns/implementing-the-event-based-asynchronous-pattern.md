---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: ea4dd376cfeda6a9f05e45940fac91abd2d4f22e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925370"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="539ad-102">Implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="539ad-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="539ad-103">Jeśli piszesz klasy z niektórych operacji, które może spowodować naliczenie zauważalnego opóźnienia, należy wziąć pod uwagę nadając mu funkcje asynchroniczne z zastosowaniem [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="539ad-104">Asynchroniczny wzorzec oparty na zdarzeniach udostępnia standardowy sposób pakietu klasę, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="539ad-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="539ad-105">Jeśli implementowane za pomocą klas pomocniczych, takich jak <xref:System.ComponentModel.AsyncOperationManager>, klasa będzie działać poprawnie w dowolnym modelu aplikacji, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplikacji konsoli i aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="539ad-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="539ad-106">Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="539ad-107">Dla prostych operacji asynchronicznych, może się okazać <xref:System.ComponentModel.BackgroundWorker> odpowiedniego składnika.</span><span class="sxs-lookup"><span data-stu-id="539ad-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="539ad-108">Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker>, zobacz [porady: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="539ad-109">Na poniższej liście opisano funkcje oparte na zdarzeniach wzorca asynchronicznego omówione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="539ad-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="539ad-110">Możliwości implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="539ad-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="539ad-111">Nazwy metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="539ad-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="539ad-112">Opcjonalnie obsługują anulowania</span><span class="sxs-lookup"><span data-stu-id="539ad-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="539ad-113">Opcjonalnie obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="539ad-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="539ad-114">Opcjonalnie zapewnia obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="539ad-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="539ad-115">Opcjonalnie zapewnia obsługę zwracania wyników przyrostowe</span><span class="sxs-lookup"><span data-stu-id="539ad-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="539ad-116">Obsługa się i parametry Ref w metodach</span><span class="sxs-lookup"><span data-stu-id="539ad-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="539ad-117">Możliwości implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="539ad-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="539ad-118">Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach — gdy:</span><span class="sxs-lookup"><span data-stu-id="539ad-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="539ad-119">Nie ma potrzeby klientów klasy <xref:System.Threading.WaitHandle> i <xref:System.IAsyncResult> obiektów dostępnych dla operacji asynchronicznych, co oznacza, że sondowania i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> musi być tworzone przez klienta.</span><span class="sxs-lookup"><span data-stu-id="539ad-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="539ad-120">Chcesz, aby operacje asynchroniczne, które mają być zarządzane przez klienta za pomocą dobrze znanych delegat wydarzenia/modelu.</span><span class="sxs-lookup"><span data-stu-id="539ad-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="539ad-121">Wszelkie działania jest kandydatem do implementacji asynchronicznego, ale należy rozważyć te spodziewasz się ponieść długie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="539ad-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="539ad-122">Dostępne są szczególnie odpowiednie operacje, w których klienci wywołania metody oraz powiadomienie po zakończeniu, bez potrzeby interwencji dalsze.</span><span class="sxs-lookup"><span data-stu-id="539ad-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="539ad-123">Odpowiednie są także działań, które w sposób ciągły, uruchamianie, okresowe powiadamiania klientów postępu, przyrostowe wyników lub zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="539ad-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="539ad-124">Aby uzyskać więcej informacji o podjęcie decyzji na potrzeby obsługi wzorca asynchronicznego opartego na zdarzeniach, zobacz [podejmowania decyzji podczas implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="539ad-125">Nazwy metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="539ad-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="539ad-126">Dla każdej metody synchronicznej *MethodName* dla którego chcesz zapewnić odpowiednika asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="539ad-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="539ad-127">Zdefiniuj *MethodName *** Async** metoda który:</span><span class="sxs-lookup"><span data-stu-id="539ad-127">Define a *MethodName***Async** method that:</span></span>  
  
-   <span data-ttu-id="539ad-128">Zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="539ad-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="539ad-129">Przyjmuje te same parametry jako *MethodName* metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="539ad-130">Akceptuje wiele wywołań.</span><span class="sxs-lookup"><span data-stu-id="539ad-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="539ad-131">Opcjonalnie zdefiniowanie *MethodName *** Async** przeciążenia, taka sama jak * MethodName ***Async**, ale o dodatkowy parametr zwracającej obiekt o nazwie `userState`.</span><span class="sxs-lookup"><span data-stu-id="539ad-131">Optionally define a *MethodName***Async** overload, identical to *MethodName***Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="539ad-132">To zrobić, jeśli masz przygotowany do zarządzania wielu równoczesnych wywołań metodę, w którym to przypadku `userState` wartości, które zostaną dostarczone do wszystkich procedur obsługi zdarzeń w celu odróżnienia wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="539ad-133">Możesz również w tym celu po prostu jako miejsce do przechowywania stanu użytkownika na nowsze pobierania.</span><span class="sxs-lookup"><span data-stu-id="539ad-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="539ad-134">Dla każdego oddzielnego *MethodName *** Async** sygnatury metody:</span><span class="sxs-lookup"><span data-stu-id="539ad-134">For each separate *MethodName***Async** method signature:</span></span>  
  
1.  <span data-ttu-id="539ad-135">W tej samej klasy jako metodę, należy zdefiniować następujące zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="539ad-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="539ad-136">Zdefiniuj następujące delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="539ad-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="539ad-137">Te prawdopodobnie zostanie zdefiniowany, poza samej klasy, ale w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="539ad-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
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
  
    -   <span data-ttu-id="539ad-138">Upewnij się, że *MethodName *** CompletedEventArgs** klasa udostępnia jej elementów członkowskich jako właściwości tylko do odczytu, a nie pola jako pola Zapobiegaj powiązaniu danych.</span><span class="sxs-lookup"><span data-stu-id="539ad-138">Ensure that the *MethodName***CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="539ad-139">Nie definiują <xref:System.ComponentModel.AsyncCompletedEventArgs>-pochodnych klas do metody, które nie dawać wyników.</span><span class="sxs-lookup"><span data-stu-id="539ad-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="539ad-140">Po prostu użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> sam.</span><span class="sxs-lookup"><span data-stu-id="539ad-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="539ad-141">Doskonale dopuszczalne jest, gdy jest to możliwe i właściwe ponownie użyć delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów.</span><span class="sxs-lookup"><span data-stu-id="539ad-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="539ad-142">W tym przypadku nazewnictwo nie będzie jako zgodne z nazwy metody od danego delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie będzie powiązany do pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="539ad-143">Opcjonalnie obsługują anulowania</span><span class="sxs-lookup"><span data-stu-id="539ad-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="539ad-144">Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, powinny zostać ujawnione anulowania do klienta, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="539ad-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="539ad-145">Należy zwrócić uwagę na to, że istnieją dwa punkty decyzyjne, które trzeba osiągnąć przed zdefiniowaniem dział pomocy technicznej Twojej anulowania:</span><span class="sxs-lookup"><span data-stu-id="539ad-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="539ad-146">Klasy, w tym przyszłych przewidywanego dodatki, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?</span><span class="sxs-lookup"><span data-stu-id="539ad-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="539ad-147">Czy operacje asynchroniczne, obsługujące wiele oczekujących operacji obsługi anulowania?</span><span class="sxs-lookup"><span data-stu-id="539ad-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="539ad-148">Oznacza to, że jest *MethodName *** Async** take metoda `userState` parametru i zezwala na wiele wywołań przed oczekiwania na zakończenie?</span><span class="sxs-lookup"><span data-stu-id="539ad-148">That is, does the *MethodName***Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="539ad-149">Użyj odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, jakie powinny być podpis dla wybranej metody anulowania.</span><span class="sxs-lookup"><span data-stu-id="539ad-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="539ad-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="539ad-150">Visual Basic</span></span>  
  
||<span data-ttu-id="539ad-151">Wiele jednoczesnych operacji obsługiwane</span><span class="sxs-lookup"><span data-stu-id="539ad-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="539ad-152">Tylko jedną operację naraz</span><span class="sxs-lookup"><span data-stu-id="539ad-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="539ad-153">Jednej operacji asynchronicznych w całej klasy</span><span class="sxs-lookup"><span data-stu-id="539ad-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="539ad-154">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="539ad-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="539ad-155">C#</span><span class="sxs-lookup"><span data-stu-id="539ad-155">C#</span></span>  
  
||<span data-ttu-id="539ad-156">Wiele jednoczesnych operacji obsługiwane</span><span class="sxs-lookup"><span data-stu-id="539ad-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="539ad-157">Tylko jedną operację naraz</span><span class="sxs-lookup"><span data-stu-id="539ad-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="539ad-158">Jednej operacji asynchronicznych w całej klasy</span><span class="sxs-lookup"><span data-stu-id="539ad-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="539ad-159">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="539ad-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="539ad-160">Jeśli zdefiniujesz `CancelAsync(object userState)` metody klientów należy zachować ostrożność, wybierając ich wartości stanu, aby były one zdolne do rozróżniania wszystkich metod asynchronicznych, wywołana dla obiektu, a nie tylko między wszystkie wywołania jednej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="539ad-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="539ad-161">Decyzja o nazwę wersji pojedynczego asynchronicznych operacji *MethodName *** AsyncCancel** opiera się na możliwości łatwiej odnaleźć metody w środowisku projektowania, takie jak technologia IntelliSense programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="539ad-161">The decision to name the single-async-operation version *MethodName***AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="539ad-162">Grupuje pokrewne elementy członkowskie, a odróżnia je od innych użytkowników, które mają one nic wspólnego z funkcji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="539ad-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="539ad-163">Jeśli spodziewasz się, że mogą istnieć dodatkowe dodany operacji asynchronicznych w kolejnych wersjach to lepiej zdefiniować `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="539ad-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="539ad-164">Nie zostaną zdefiniowane z powyższej tabeli na wiele sposobów w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="539ad-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="539ad-165">Który nie ma sensu lub go będzie zbliżyć do siebie te interfejsu klasy za pomocą rozprzestrzenianie metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="539ad-166">Tych metodach zwykle zwróci natychmiast i operację może lub nie może w rzeczywistości anulować.</span><span class="sxs-lookup"><span data-stu-id="539ad-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="539ad-167">W procedurze obsługi zdarzeń dla *MethodName *** Ukończono** zdarzenia *MethodName *** CompletedEventArgs** obiekt zawiera `Cancelled` pola, które klienci mogą używać, aby określić, czy nastąpiło anulowanie.</span><span class="sxs-lookup"><span data-stu-id="539ad-167">In the event handler for the *MethodName***Completed** event, the *MethodName***CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="539ad-168">Przestrzeganie semantyki anulowania opisanego w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="539ad-169">Opcjonalnie obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="539ad-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="539ad-170">Jeśli klasa nie obsługuje wielu równoczesnych wywołań, należy rozważyć uwidocznienie `IsBusy` właściwości.</span><span class="sxs-lookup"><span data-stu-id="539ad-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="539ad-171">Dzięki temu deweloperzy mogą określić, czy *MethodName *** Async** metodą jest uruchomienie bez przechwytywanie wyjątku z *MethodName *** Async** metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-171">This allows developers to determine whether a *MethodName***Async** method is running without catching an exception from the *MethodName***Async** method.</span></span>  
  
 <span data-ttu-id="539ad-172">Przestrzeganie `IsBusy` semantyki opisanego w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="539ad-173">Opcjonalnie zapewnia obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="539ad-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="539ad-174">Jest często pożądane dla operacji asynchronicznej do raportowania postępu podczas jego działania.</span><span class="sxs-lookup"><span data-stu-id="539ad-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="539ad-175">Asynchroniczny wzorzec oparty na zdarzeniach przedstawiono wskazówki, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="539ad-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="539ad-176">Opcjonalnie zdefiniowanie zdarzenia wygenerowane przez operację asynchroniczną i wywoływane dla odpowiedniego wątku.</span><span class="sxs-lookup"><span data-stu-id="539ad-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="539ad-177"><xref:System.ComponentModel.ProgressChangedEventArgs> Obiektu niesie ze sobą wskaźnik postępu wartości całkowitych, który powinien należeć do zakresu od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="539ad-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="539ad-178">Nazwa tego zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="539ad-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="539ad-179">`ProgressChanged` Jeśli klasa ma wiele operacji asynchronicznych (lub oczekuje się, że powiększona i obejmie wiele operacji asynchronicznych w przyszłych wersjach)</span><span class="sxs-lookup"><span data-stu-id="539ad-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="539ad-180">*MethodName *** ProgressChanged** Jeśli klasa ma jedną operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="539ad-180">*MethodName***ProgressChanged** if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="539ad-181">Ten wybór nazewnictwa równoleżnikami zgłaszający metody anulowania, zgodnie z opisem w sekcji opcjonalnie anulowania obsługi.</span><span class="sxs-lookup"><span data-stu-id="539ad-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="539ad-182">Skorzystaj z tego zdarzenia <xref:System.ComponentModel.ProgressChangedEventHandler> podpis delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="539ad-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="539ad-183">Alternatywnie, jeśli można podać wskaźnik postępu bardziej specyficznego dla domeny (w przypadku wystąpienia, Bajty odczytane i całkowita liczba bajtów dla operacji pobierania), następnie należy zdefiniować klasę pochodną z <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="539ad-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="539ad-184">Należy pamiętać, że istnieje tylko jeden `ProgressChanged` lub *MethodName *** ProgressChanged** zdarzeń dla tej klasy, niezależnie od liczby metod asynchronicznych, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="539ad-184">Note that there is only one `ProgressChanged` or *MethodName***ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="539ad-185">Klienci powinni używać `userState` obiekt, który jest przekazywany do *MethodName *** Async** metody w celu rozróżnienia aktualizacji w toku na wiele jednoczesnych operacji.</span><span class="sxs-lookup"><span data-stu-id="539ad-185">Clients are expected to use the `userState` object that is passed to the *MethodName***Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="539ad-186">Mogą wystąpić sytuacje, w których wiele operacji obsługi postępu, a każda zwraca inny wskaźnik postępu.</span><span class="sxs-lookup"><span data-stu-id="539ad-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="539ad-187">W tym przypadku jeden `ProgressChanged` zdarzeń nie jest odpowiednie, a może rozważyć, obsługa wielu `ProgressChanged` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="539ad-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="539ad-188">W tym przypadku użyj wzorzec nazewnictwa *MethodName *** ProgressChanged** dla każdego *MethodName *** Async** metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-188">In this case use a naming pattern of *MethodName***ProgressChanged** for each *MethodName***Async** method.</span></span>  
  
 <span data-ttu-id="539ad-189">Przestrzeganie semantykę raportowania postępu opisane [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="539ad-190">Opcjonalnie zapewnia obsługę zwracania wyników przyrostowe</span><span class="sxs-lookup"><span data-stu-id="539ad-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="539ad-191">Czasami operacji asynchronicznej może zwrócić wyniki przyrostową przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="539ad-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="539ad-192">Istnieje kilka opcji, które mogą służyć do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="539ad-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="539ad-193">Oto niektóre przykłady.</span><span class="sxs-lookup"><span data-stu-id="539ad-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="539ad-194">Jednym operation — klasa</span><span class="sxs-lookup"><span data-stu-id="539ad-194">Single-operation Class</span></span>  
 <span data-ttu-id="539ad-195">Jeśli klasa obsługuje tylko jedną operację asynchroniczną, a tej operacji jest w stanie zwracają przyrostowe, następnie:</span><span class="sxs-lookup"><span data-stu-id="539ad-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="539ad-196">Rozszerzanie <xref:System.ComponentModel.ProgressChangedEventArgs> wpisz do przenoszenia danych przyrostowych wyników, a następnie zdefiniuj *MethodName *** ProgressChanged** zdarzeń za pomocą rozszerzenia danych.</span><span class="sxs-lookup"><span data-stu-id="539ad-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName***ProgressChanged** event with this extended data.</span></span>  
  
-   <span data-ttu-id="539ad-197">Wywoływanie to *MethodName *** ProgressChanged** zdarzenie, kiedy ma wynik przyrostowe do raportu.</span><span class="sxs-lookup"><span data-stu-id="539ad-197">Raise this *MethodName***ProgressChanged** event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="539ad-198">To rozwiązanie odnosi się do klasy pojedynczej asynchronicznych operacji ponieważ nie istnieje żaden problem za pomocą tego samego zdarzenia występujące w celu zwracania wyników przyrostowych na "wszystkie operacje", jako *MethodName *** ProgressChanged** jest zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="539ad-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName***ProgressChanged** event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="539ad-199">Klasa wielu operacji z jednorodnych wyniki przyrostowe</span><span class="sxs-lookup"><span data-stu-id="539ad-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="539ad-200">W takim przypadku klasa obsługuje wiele metod asynchronicznych, każdy może zwracanie wyników przyrostowe i przyrostowe wyniki te wszystkie mają ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="539ad-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="539ad-201">Postępuj zgodnie z modelem opisane powyżej, aby klasy pojedynczej operacji, taka sama <xref:System.EventArgs> struktury będzie działać w przypadku wszystkich wyników przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="539ad-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="539ad-202">Zdefiniuj `ProgressChanged` zdarzeń zamiast *MethodName *** ProgressChanged** zdarzenie, ponieważ dotyczy on wiele metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="539ad-202">Define a `ProgressChanged` event instead of a *MethodName***ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="539ad-203">Klasa wielu operacji z heterogenicznych wyniki przyrostowe</span><span class="sxs-lookup"><span data-stu-id="539ad-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="539ad-204">Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwraca innego typu danych, należy:</span><span class="sxs-lookup"><span data-stu-id="539ad-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="539ad-205">Oddziel wynik Twojego przyrostowe raportów z raportowania postępu.</span><span class="sxs-lookup"><span data-stu-id="539ad-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="539ad-206">Zdefiniuj oddzielnego *MethodName *** ProgressChanged** zdarzeń z odpowiednich <xref:System.EventArgs> dla poszczególnych metod asynchronicznych do obsługi danych przyrostowych wyniku tej metody.</span><span class="sxs-lookup"><span data-stu-id="539ad-206">Define a separate *MethodName***ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="539ad-207">Wywoływanie tej obsługi zdarzeń w odpowiednich wątku, zgodnie z opisem w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="539ad-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="539ad-208">Obsługa się i parametry Ref w metodach</span><span class="sxs-lookup"><span data-stu-id="539ad-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="539ad-209">Mimo że korzystanie z `out` i `ref` jest, ogólnie rzecz biorąc, zalecane w programie .NET Framework, poniżej przedstawiono reguły, które należy wykonać podczas są obecne:</span><span class="sxs-lookup"><span data-stu-id="539ad-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="539ad-210">Podana metoda synchroniczna *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="539ad-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="539ad-211">`out` Parametry *MethodName* nie powinna być częścią *MethodName ***Async**. Zamiast tego powinien być częścią *MethodName *** CompletedEventArgs**  z taką samą nazwę jak parametr równoważne w *MethodName* (chyba że istnieje bardziej odpowiednie nazwy).</span><span class="sxs-lookup"><span data-stu-id="539ad-211">`out` parameters to *MethodName* should not be part of *MethodName***Async**. Instead, they should be part of *MethodName***CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="539ad-212">`ref` Parametry *MethodName* powinny się wyświetlać jako część *MethodName ***Async**oraz jako część *MethodName *** CompletedEventArgs**  z taką samą nazwę jak parametr równoważne w *MethodName* (chyba że istnieje bardziej odpowiednie nazwy).</span><span class="sxs-lookup"><span data-stu-id="539ad-212">`ref` parameters to *MethodName* should appear as part of *MethodName***Async**, and as part of *MethodName***CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="539ad-213">Na przykład biorąc pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="539ad-213">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="539ad-214">Metoda asynchronicznego i jego <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="539ad-214">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="539ad-215">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="539ad-215">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="539ad-216">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="539ad-216">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="539ad-217">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="539ad-217">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="539ad-218">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="539ad-218">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="539ad-219">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="539ad-219">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="539ad-220">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="539ad-220">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="539ad-221">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="539ad-221">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
