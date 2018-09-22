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
ms.openlocfilehash: 3cb38cd9d7b27ab28b602e4e4c813d58d904abd3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584139"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="d9e8d-102">Implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="d9e8d-103">Jeśli piszesz klasy z niektórych operacji, które może spowodować naliczenie zauważalnego opóźnienia, należy wziąć pod uwagę nadając mu funkcje asynchroniczne z zastosowaniem [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="d9e8d-104">Asynchroniczny wzorzec oparty na zdarzeniach udostępnia standardowy sposób pakietu klasę, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="d9e8d-105">Jeśli implementowane za pomocą klas pomocniczych, takich jak <xref:System.ComponentModel.AsyncOperationManager>, klasa będzie działać poprawnie w dowolnym modelu aplikacji, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplikacji konsoli i aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="d9e8d-106">Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="d9e8d-107">Dla prostych operacji asynchronicznych, może się okazać <xref:System.ComponentModel.BackgroundWorker> odpowiedniego składnika.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="d9e8d-108">Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker>, zobacz [porady: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="d9e8d-109">Na poniższej liście opisano funkcje oparte na zdarzeniach wzorca asynchronicznego omówione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="d9e8d-110">Możliwości implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="d9e8d-111">Nazwy metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="d9e8d-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="d9e8d-112">Opcjonalnie obsługują anulowania</span><span class="sxs-lookup"><span data-stu-id="d9e8d-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="d9e8d-113">Opcjonalnie obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="d9e8d-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="d9e8d-114">Opcjonalnie zapewnia obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="d9e8d-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="d9e8d-115">Opcjonalnie zapewnia obsługę zwracania wyników przyrostowe</span><span class="sxs-lookup"><span data-stu-id="d9e8d-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="d9e8d-116">Obsługa się i parametry Ref w metodach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="d9e8d-117">Możliwości implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="d9e8d-118">Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach — gdy:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="d9e8d-119">Nie ma potrzeby klientów klasy <xref:System.Threading.WaitHandle> i <xref:System.IAsyncResult> obiektów dostępnych dla operacji asynchronicznych, co oznacza, że sondowania i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> musi być tworzone przez klienta.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="d9e8d-120">Chcesz, aby operacje asynchroniczne, które mają być zarządzane przez klienta za pomocą dobrze znanych delegat wydarzenia/modelu.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="d9e8d-121">Wszelkie działania jest kandydatem do implementacji asynchronicznego, ale należy rozważyć te spodziewasz się ponieść długie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="d9e8d-122">Dostępne są szczególnie odpowiednie operacje, w których klienci wywołania metody oraz powiadomienie po zakończeniu, bez potrzeby interwencji dalsze.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="d9e8d-123">Odpowiednie są także działań, które w sposób ciągły, uruchamianie, okresowe powiadamiania klientów postępu, przyrostowe wyników lub zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="d9e8d-124">Aby uzyskać więcej informacji o podjęcie decyzji na potrzeby obsługi wzorca asynchronicznego opartego na zdarzeniach, zobacz [podejmowania decyzji podczas implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="d9e8d-125">Nazwy metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="d9e8d-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="d9e8d-126">Dla każdej metody synchronicznej *MethodName* dla którego chcesz zapewnić odpowiednika asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="d9e8d-127">Zdefiniuj _MethodName_**Async** metoda który:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-127">Define a _MethodName_**Async** method that:</span></span>  
  
-   <span data-ttu-id="d9e8d-128">Zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="d9e8d-129">Przyjmuje te same parametry jako *MethodName* metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="d9e8d-130">Akceptuje wiele wywołań.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="d9e8d-131">Opcjonalnie zdefiniowanie _MethodName_**Async** przeciążenia, taka sama jak _MethodName_**Async**, ale z dodatkową zwracającej obiekt Parametr o nazwie `userState`.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="d9e8d-132">To zrobić, jeśli masz przygotowany do zarządzania wielu równoczesnych wywołań metodę, w którym to przypadku `userState` wartości, które zostaną dostarczone do wszystkich procedur obsługi zdarzeń w celu odróżnienia wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="d9e8d-133">Możesz również w tym celu po prostu jako miejsce do przechowywania stanu użytkownika na nowsze pobierania.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="d9e8d-134">Dla każdego oddzielnego _MethodName_**Async** sygnatury metody:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-134">For each separate _MethodName_**Async** method signature:</span></span>  
  
1.  <span data-ttu-id="d9e8d-135">W tej samej klasy jako metodę, należy zdefiniować następujące zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="d9e8d-136">Zdefiniuj następujące delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="d9e8d-137">Te prawdopodobnie zostanie zdefiniowany, poza samej klasy, ale w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
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
  
    -   <span data-ttu-id="d9e8d-138">Upewnij się, że _MethodName_**CompletedEventArgs** klasa udostępnia jej elementów członkowskich jako właściwości tylko do odczytu, a nie pola jako pola Zapobiegaj powiązaniu danych.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="d9e8d-139">Nie definiują <xref:System.ComponentModel.AsyncCompletedEventArgs>-pochodnych klas do metody, które nie dawać wyników.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="d9e8d-140">Po prostu użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> sam.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d9e8d-141">Doskonale dopuszczalne jest, gdy jest to możliwe i właściwe ponownie użyć delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="d9e8d-142">W tym przypadku nazewnictwo nie będzie jako zgodne z nazwy metody od danego delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie będzie powiązany do pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="d9e8d-143">Opcjonalnie obsługują anulowania</span><span class="sxs-lookup"><span data-stu-id="d9e8d-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="d9e8d-144">Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, powinny zostać ujawnione anulowania do klienta, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="d9e8d-145">Należy zwrócić uwagę na to, że istnieją dwa punkty decyzyjne, które trzeba osiągnąć przed zdefiniowaniem dział pomocy technicznej Twojej anulowania:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="d9e8d-146">Klasy, w tym przyszłych przewidywanego dodatki, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?</span><span class="sxs-lookup"><span data-stu-id="d9e8d-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="d9e8d-147">Czy operacje asynchroniczne, obsługujące wiele oczekujących operacji obsługi anulowania?</span><span class="sxs-lookup"><span data-stu-id="d9e8d-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="d9e8d-148">Oznacza to, że jest _MethodName_**Async** take metoda `userState` parametru i zezwala na wiele wywołań przed oczekiwania na zakończenie?</span><span class="sxs-lookup"><span data-stu-id="d9e8d-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="d9e8d-149">Użyj odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, jakie powinny być podpis dla wybranej metody anulowania.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="d9e8d-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9e8d-150">Visual Basic</span></span>  
  
||<span data-ttu-id="d9e8d-151">Wiele jednoczesnych operacji obsługiwane</span><span class="sxs-lookup"><span data-stu-id="d9e8d-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="d9e8d-152">Tylko jedną operację naraz</span><span class="sxs-lookup"><span data-stu-id="d9e8d-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="d9e8d-153">Jednej operacji asynchronicznych w całej klasy</span><span class="sxs-lookup"><span data-stu-id="d9e8d-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="d9e8d-154">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="d9e8d-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="d9e8d-155">C#</span><span class="sxs-lookup"><span data-stu-id="d9e8d-155">C#</span></span>  
  
||<span data-ttu-id="d9e8d-156">Wiele jednoczesnych operacji obsługiwane</span><span class="sxs-lookup"><span data-stu-id="d9e8d-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="d9e8d-157">Tylko jedną operację naraz</span><span class="sxs-lookup"><span data-stu-id="d9e8d-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="d9e8d-158">Jednej operacji asynchronicznych w całej klasy</span><span class="sxs-lookup"><span data-stu-id="d9e8d-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="d9e8d-159">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="d9e8d-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="d9e8d-160">Jeśli zdefiniujesz `CancelAsync(object userState)` metody klientów należy zachować ostrożność, wybierając ich wartości stanu, aby były one zdolne do rozróżniania wszystkich metod asynchronicznych, wywołana dla obiektu, a nie tylko między wszystkie wywołania jednej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="d9e8d-161">Decyzja o nazwę wersji pojedynczego asynchronicznych operacji _MethodName_**AsyncCancel** opiera się na możliwości łatwiej odnaleźć metody w środowisku projektowania, takie jak technologia IntelliSense programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="d9e8d-162">Grupuje pokrewne elementy członkowskie, a odróżnia je od innych użytkowników, które mają one nic wspólnego z funkcji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="d9e8d-163">Jeśli spodziewasz się, że mogą istnieć dodatkowe dodany operacji asynchronicznych w kolejnych wersjach to lepiej zdefiniować `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="d9e8d-164">Nie zostaną zdefiniowane z powyższej tabeli na wiele sposobów w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="d9e8d-165">Który nie ma sensu lub go będzie zbliżyć do siebie te interfejsu klasy za pomocą rozprzestrzenianie metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="d9e8d-166">Tych metodach zwykle zwróci natychmiast i operację może lub nie może w rzeczywistości anulować.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="d9e8d-167">W procedurze obsługi zdarzeń dla _MethodName_**Ukończono** zdarzenia _MethodName_**CompletedEventArgs** obiekt zawiera `Cancelled` pola, które klienci mogą używać do określenia, czy nastąpiło anulowanie.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="d9e8d-168">Przestrzeganie semantyki anulowania opisanego w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="d9e8d-169">Opcjonalnie obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="d9e8d-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="d9e8d-170">Jeśli klasa nie obsługuje wielu równoczesnych wywołań, należy rozważyć uwidocznienie `IsBusy` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="d9e8d-171">Dzięki temu deweloperzy mogą określić, czy _MethodName_**Async** bez przechwytywanie wyjątku z uruchomiona jest metoda _MethodName_**Async**  metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>  
  
 <span data-ttu-id="d9e8d-172">Przestrzeganie `IsBusy` semantyki opisanego w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="d9e8d-173">Opcjonalnie zapewnia obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="d9e8d-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="d9e8d-174">Jest często pożądane dla operacji asynchronicznej do raportowania postępu podczas jego działania.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="d9e8d-175">Asynchroniczny wzorzec oparty na zdarzeniach przedstawiono wskazówki, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="d9e8d-176">Opcjonalnie zdefiniowanie zdarzenia wygenerowane przez operację asynchroniczną i wywoływane dla odpowiedniego wątku.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="d9e8d-177"><xref:System.ComponentModel.ProgressChangedEventArgs> Obiektu niesie ze sobą wskaźnik postępu wartości całkowitych, który powinien należeć do zakresu od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="d9e8d-178">Nazwa tego zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="d9e8d-179">`ProgressChanged` Jeśli klasa ma wiele operacji asynchronicznych (lub oczekuje się, że powiększona i obejmie wiele operacji asynchronicznych w przyszłych wersjach)</span><span class="sxs-lookup"><span data-stu-id="d9e8d-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="d9e8d-180">_MethodName_**ProgressChanged** Jeśli klasa ma jedną operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="d9e8d-181">Ten wybór nazewnictwa równoleżnikami zgłaszający metody anulowania, zgodnie z opisem w sekcji opcjonalnie anulowania obsługi.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="d9e8d-182">Skorzystaj z tego zdarzenia <xref:System.ComponentModel.ProgressChangedEventHandler> podpis delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="d9e8d-183">Alternatywnie, jeśli można podać wskaźnik postępu bardziej specyficznego dla domeny (w przypadku wystąpienia, Bajty odczytane i całkowita liczba bajtów dla operacji pobierania), następnie należy zdefiniować klasę pochodną z <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="d9e8d-184">Należy pamiętać, że istnieje tylko jeden `ProgressChanged` lub _MethodName_**ProgressChanged** zdarzenia dla tej klasy, niezależnie od liczby metod asynchronicznych, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="d9e8d-185">Klienci powinni używać `userState` obiekt, który jest przekazywany do _MethodName_**Async** metody w celu rozróżnienia aktualizacji w toku na wiele jednoczesnych operacji.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="d9e8d-186">Mogą wystąpić sytuacje, w których wiele operacji obsługi postępu, a każda zwraca inny wskaźnik postępu.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="d9e8d-187">W tym przypadku jeden `ProgressChanged` zdarzeń nie jest odpowiednie, a może rozważyć, obsługa wielu `ProgressChanged` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="d9e8d-188">W tym przypadku użyj wzorzec nazewnictwa _MethodName_**ProgressChanged** dla każdego _MethodName_**Async** metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>  
  
 <span data-ttu-id="d9e8d-189">Przestrzeganie semantykę raportowania postępu opisane [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="d9e8d-190">Opcjonalnie zapewnia obsługę zwracania wyników przyrostowe</span><span class="sxs-lookup"><span data-stu-id="d9e8d-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="d9e8d-191">Czasami operacji asynchronicznej może zwrócić wyniki przyrostową przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="d9e8d-192">Istnieje kilka opcji, które mogą służyć do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="d9e8d-193">Oto niektóre przykłady.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="d9e8d-194">Jednym operation — klasa</span><span class="sxs-lookup"><span data-stu-id="d9e8d-194">Single-operation Class</span></span>  
 <span data-ttu-id="d9e8d-195">Jeśli klasa obsługuje tylko jedną operację asynchroniczną, a tej operacji jest w stanie zwracają przyrostowe, następnie:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="d9e8d-196">Rozszerzanie <xref:System.ComponentModel.ProgressChangedEventArgs> wpisz do przenoszenia danych przyrostowych wyników, a następnie zdefiniuj _MethodName_**ProgressChanged** zdarzeń za pomocą rozszerzenia danych.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>  
  
-   <span data-ttu-id="d9e8d-197">Wywoływanie to _MethodName_**ProgressChanged** zdarzenie, kiedy ma wynik przyrostowe do raportu.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="d9e8d-198">To rozwiązanie odnosi się do klasy pojedynczej asynchronicznych operacji ponieważ nie istnieje żaden problem za pomocą tego samego zdarzenia występujące w celu zwracania wyników przyrostowych na "wszystkie operacje", jako _MethodName_**ProgressChanged**  jest zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="d9e8d-199">Klasa wielu operacji z jednorodnych wyniki przyrostowe</span><span class="sxs-lookup"><span data-stu-id="d9e8d-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="d9e8d-200">W takim przypadku klasa obsługuje wiele metod asynchronicznych, każdy może zwracanie wyników przyrostowe i przyrostowe wyniki te wszystkie mają ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="d9e8d-201">Postępuj zgodnie z modelem opisane powyżej, aby klasy pojedynczej operacji, taka sama <xref:System.EventArgs> struktury będzie działać w przypadku wszystkich wyników przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="d9e8d-202">Zdefiniuj `ProgressChanged` zdarzeń zamiast _MethodName_**ProgressChanged** zdarzenie, ponieważ dotyczy on wiele metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="d9e8d-203">Klasa wielu operacji z heterogenicznych wyniki przyrostowe</span><span class="sxs-lookup"><span data-stu-id="d9e8d-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="d9e8d-204">Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwraca innego typu danych, należy:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="d9e8d-205">Oddziel wynik Twojego przyrostowe raportów z raportowania postępu.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="d9e8d-206">Zdefiniuj oddzielnego _MethodName_**ProgressChanged** zdarzeń z odpowiednich <xref:System.EventArgs> dla poszczególnych metod asynchronicznych do obsługi danych przyrostowych wyniku tej metody.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="d9e8d-207">Wywoływanie tej obsługi zdarzeń w odpowiednich wątku, zgodnie z opisem w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="d9e8d-208">Obsługa się i parametry Ref w metodach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="d9e8d-209">Mimo że korzystanie z `out` i `ref` jest, ogólnie rzecz biorąc, zalecane w programie .NET Framework, poniżej przedstawiono reguły, które należy wykonać podczas są obecne:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="d9e8d-210">Podana metoda synchroniczna *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="d9e8d-211">`out` Parametry *MethodName* nie powinna być częścią _MethodName_**Async**.</span><span class="sxs-lookup"><span data-stu-id="d9e8d-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="d9e8d-212">Zamiast tego powinien być częścią _MethodName_**CompletedEventArgs** z taką samą nazwę jak parametr równoważne w *MethodName* (chyba że istnieje bardziej odpowiednie Nazwa).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="d9e8d-213">`ref` Parametry *MethodName* powinny się wyświetlać jako część _MethodName_**Async**oraz jako część _MethodName_  **CompletedEventArgs** z taką samą nazwę jak parametr równoważne w *MethodName* (chyba że istnieje bardziej odpowiednie nazwy).</span><span class="sxs-lookup"><span data-stu-id="d9e8d-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="d9e8d-214">Na przykład biorąc pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="d9e8d-215">Metoda asynchronicznego i jego <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d9e8d-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9e8d-216">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9e8d-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>  
- <xref:System.ComponentModel.AsyncCompletedEventArgs>  
- [<span data-ttu-id="d9e8d-217">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [<span data-ttu-id="d9e8d-218">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="d9e8d-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [<span data-ttu-id="d9e8d-219">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="d9e8d-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
- [<span data-ttu-id="d9e8d-220">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9e8d-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
- [<span data-ttu-id="d9e8d-221">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d9e8d-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [<span data-ttu-id="d9e8d-222">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="d9e8d-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
