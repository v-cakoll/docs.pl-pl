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
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663708"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="d1f94-102">Implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d1f94-102">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="d1f94-103">Jeśli piszesz klasę z niektórych operacji, które mogą ponosić zauważalne opóźnienia, należy rozważyć nadanie jej funkcji asynchronicznych, implementując [omówienie asynchronicznego wzorca opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d1f94-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="d1f94-104">Wzorzec asynchroniczny oparty na zdarzeniach zapewnia znormalizowany sposób pakowania klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="d1f94-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="d1f94-105">Jeśli zaimplementowane z <xref:System.ComponentModel.AsyncOperationManager>klas pomocnika, takich jak , klasa będzie działać poprawnie w dowolnym modelu aplikacji, w tym ASP.NET, aplikacji konsoli i aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d1f94-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="d1f94-106">Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [Jak: Implementowanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d1f94-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="d1f94-107">W przypadku prostych operacji asynchronicznych <xref:System.ComponentModel.BackgroundWorker> może się okazać, że składnik jest odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="d1f94-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="d1f94-108">Aby uzyskać <xref:System.ComponentModel.BackgroundWorker>więcej informacji na temat , zobacz [Jak: Uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="d1f94-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="d1f94-109">Na poniższej liście opisano funkcje wzorca asynchronicznego opartego na zdarzeniach omówione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d1f94-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="d1f94-110">Możliwości implementowania wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d1f94-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="d1f94-111">Nazywanie metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="d1f94-111">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="d1f94-112">Opcjonalnie obsługa anulowania</span><span class="sxs-lookup"><span data-stu-id="d1f94-112">Optionally Support Cancellation</span></span>

- <span data-ttu-id="d1f94-113">Opcjonalnie obsługa isbusy właściwość</span><span class="sxs-lookup"><span data-stu-id="d1f94-113">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="d1f94-114">Opcjonalnie zapewnij obsługę raportowania postępów</span><span class="sxs-lookup"><span data-stu-id="d1f94-114">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="d1f94-115">Opcjonalnie zapewnij obsługę zwracania wyników przyrostowych</span><span class="sxs-lookup"><span data-stu-id="d1f94-115">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="d1f94-116">Obsługa parametrów out i ref w metodach</span><span class="sxs-lookup"><span data-stu-id="d1f94-116">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="d1f94-117">Możliwości implementowania wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d1f94-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="d1f94-118">Należy rozważyć wdrożenie wzorca asynchronicznego opartego na zdarzeniach, gdy:</span><span class="sxs-lookup"><span data-stu-id="d1f94-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="d1f94-119">Klienci klasy nie potrzebują <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> i obiekty dostępne dla operacji asynchronicznych, co oznacza, że sondowanie i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> będą musiały być tworzone przez klienta.</span><span class="sxs-lookup"><span data-stu-id="d1f94-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="d1f94-120">Operacje asynchroniczne mają być zarządzane przez klienta za pomocą znanego modelu zdarzenia/delegata.</span><span class="sxs-lookup"><span data-stu-id="d1f94-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="d1f94-121">Każda operacja jest kandydatem do implementacji asynchronicznej, ale te, które można oczekiwać, aby ponieść długie opóźnienia powinny być brane pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="d1f94-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="d1f94-122">Szczególnie odpowiednie są operacje, w których klienci dzwonią metodą i są powiadamiani po zakończeniu, bez konieczności dalszej interwencji.</span><span class="sxs-lookup"><span data-stu-id="d1f94-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="d1f94-123">Odpowiednie są również operacje, które są uruchamiane w sposób ciągły, okresowo powiadamiając klientów o postępie, wynikach przyrostowych lub zmianach stanu.</span><span class="sxs-lookup"><span data-stu-id="d1f94-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="d1f94-124">Aby uzyskać więcej informacji na temat podejmowania decyzji, kiedy obsługiwać wzorzec asynchroniczny oparty na zdarzeniach, zobacz [Decydowanie o wdrożeniu wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d1f94-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="d1f94-125">Nazywanie metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="d1f94-125">Naming Asynchronous Methods</span></span>

<span data-ttu-id="d1f94-126">Dla każdej metody synchronicznej *MethodName,* dla której chcesz podać odpowiednik asynchroniczny:</span><span class="sxs-lookup"><span data-stu-id="d1f94-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="d1f94-127">Zdefiniuj metodę**Asynia** _MethodName,_ która:</span><span class="sxs-lookup"><span data-stu-id="d1f94-127">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="d1f94-128">Zwraca wartość `void`.</span><span class="sxs-lookup"><span data-stu-id="d1f94-128">Returns `void`.</span></span>

- <span data-ttu-id="d1f94-129">Przyjmuje te same parametry, co *MethodName* metody.</span><span class="sxs-lookup"><span data-stu-id="d1f94-129">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="d1f94-130">Akceptuje wiele wywołań.</span><span class="sxs-lookup"><span data-stu-id="d1f94-130">Accepts multiple invocations.</span></span>

<span data-ttu-id="d1f94-131">Opcjonalnie zdefiniuj przeciążenie**Asynia** _Name MethodName,_ identyczne `userState`z _MethodName_**Async**, ale z dodatkowym parametrem o wartości obiektu o nazwie .</span><span class="sxs-lookup"><span data-stu-id="d1f94-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="d1f94-132">Wykonaj to, jeśli jesteś przygotowany do zarządzania wieloma równoczesnych wywołań `userState` metody, w którym to przypadku wartość zostanie dostarczona z powrotem do wszystkich programów obsługi zdarzeń, aby odróżnić wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d1f94-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="d1f94-133">Można również to zrobić po prostu jako miejsce do przechowywania stanu użytkownika do późniejszego pobierania.</span><span class="sxs-lookup"><span data-stu-id="d1f94-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="d1f94-134">Dla każdego oddzielnego podpisu metody _MethodName_**Async:**</span><span class="sxs-lookup"><span data-stu-id="d1f94-134">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="d1f94-135">Zdefiniuj następujące zdarzenie w tej samej klasie co metoda:</span><span class="sxs-lookup"><span data-stu-id="d1f94-135">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="d1f94-136">Zdefiniuj <xref:System.ComponentModel.AsyncCompletedEventArgs>następującego pełnomocnika i .</span><span class="sxs-lookup"><span data-stu-id="d1f94-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="d1f94-137">Będą one prawdopodobnie zdefiniowane poza samą klasą, ale w tym samym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="d1f94-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="d1f94-138">Upewnij się, że _MethodName_**CompletedEventArgs** klasy udostępnia jego elementy członkowskie jako właściwości tylko do odczytu, a nie pola, jak pola zapobiec powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="d1f94-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="d1f94-139">Nie należy <xref:System.ComponentModel.AsyncCompletedEventArgs>definiować żadnych klas pochodnych dla metod, które nie dają wyników.</span><span class="sxs-lookup"><span data-stu-id="d1f94-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="d1f94-140">Wystarczy użyć samego <xref:System.ComponentModel.AsyncCompletedEventArgs> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d1f94-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="d1f94-141">Jest całkowicie dopuszczalne, jeśli jest to wykonalne i <xref:System.ComponentModel.AsyncCompletedEventArgs> właściwe, ponowne użycie delegata i typów.</span><span class="sxs-lookup"><span data-stu-id="d1f94-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="d1f94-142">W takim przypadku nazewnictwa nie będzie tak zgodne z nazwą metody, <xref:System.ComponentModel.AsyncCompletedEventArgs> ponieważ danego delegata i nie będą powiązane z jedną metodą.</span><span class="sxs-lookup"><span data-stu-id="d1f94-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="d1f94-143">Opcjonalnie obsługa anulowania</span><span class="sxs-lookup"><span data-stu-id="d1f94-143">Optionally Support Cancellation</span></span>

<span data-ttu-id="d1f94-144">Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, anulowanie powinno być widoczne dla klienta, jak opisano poniżej.</span><span class="sxs-lookup"><span data-stu-id="d1f94-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="d1f94-145">Należy pamiętać, że istnieją dwa punkty decyzyjne, które muszą zostać osiągnięte przed zdefiniowaniem wsparcia anulowania:</span><span class="sxs-lookup"><span data-stu-id="d1f94-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="d1f94-146">Czy twoja klasa, w tym przyszłe przewidywane dodatki do niej, mają tylko jedną operację asynchroniczną, która obsługuje anulowanie?</span><span class="sxs-lookup"><span data-stu-id="d1f94-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="d1f94-147">Czy operacje asynchroniczne obsługujące anulowanie obsługują wiele oczekujących operacji?</span><span class="sxs-lookup"><span data-stu-id="d1f94-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="d1f94-148">Oznacza to, czy _MethodName_**Async** metoda podjąć `userState` parametr i czy zezwala na wiele wywołań przed oczekiwaniem na dowolne do końca?</span><span class="sxs-lookup"><span data-stu-id="d1f94-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="d1f94-149">Skorzystaj z odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, jaki powinien być podpis dla metody anulowania.</span><span class="sxs-lookup"><span data-stu-id="d1f94-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="d1f94-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1f94-150">Visual Basic</span></span>

||<span data-ttu-id="d1f94-151">Obsługa wielu równoczesnych operacji</span><span class="sxs-lookup"><span data-stu-id="d1f94-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="d1f94-152">Tylko jedna operacja naraz</span><span class="sxs-lookup"><span data-stu-id="d1f94-152">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="d1f94-153">Jedna operacja Async w całej klasie</span><span class="sxs-lookup"><span data-stu-id="d1f94-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="d1f94-154">Wiele operacji asynchronicznej w klasie</span><span class="sxs-lookup"><span data-stu-id="d1f94-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="d1f94-155">C\#</span><span class="sxs-lookup"><span data-stu-id="d1f94-155">C\#</span></span>

||<span data-ttu-id="d1f94-156">Obsługa wielu równoczesnych operacji</span><span class="sxs-lookup"><span data-stu-id="d1f94-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="d1f94-157">Tylko jedna operacja naraz</span><span class="sxs-lookup"><span data-stu-id="d1f94-157">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="d1f94-158">Jedna operacja Async w całej klasie</span><span class="sxs-lookup"><span data-stu-id="d1f94-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="d1f94-159">Wiele operacji asynchronicznej w klasie</span><span class="sxs-lookup"><span data-stu-id="d1f94-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="d1f94-160">Jeśli zdefiniujesz `CancelAsync(object userState)` metodę, klienci muszą być ostrożni podczas wybierania ich wartości stanu, aby mogły rozróżniać wszystkie metody asynchroniczne wywoływane na obiekcie, a nie tylko między wszystkimi wywołaniami pojedynczej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d1f94-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="d1f94-161">Decyzja o nazwie wersji pojedynczej operacji asynchronicznej _MethodName_**AsyncCancel** opiera się na możliwości łatwiejszego odnajdowania metody w środowisku projektowym, takim jak IntelliSense programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1f94-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="d1f94-162">To grupuje powiązanych członków i odróżnia je od innych elementów członkowskich, które nie mają nic wspólnego z funkcjami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="d1f94-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="d1f94-163">Jeśli oczekujesz, że mogą istnieć dodatkowe operacje asynchroniczne `CancelAsync`dodane w kolejnych wersjach, lepiej jest zdefiniować .</span><span class="sxs-lookup"><span data-stu-id="d1f94-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="d1f94-164">Nie należy definiować wielu metod z powyższej tabeli w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="d1f94-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="d1f94-165">To nie ma sensu, lub będzie zaśmiecać interfejs klasy z proliferacji metod.</span><span class="sxs-lookup"><span data-stu-id="d1f94-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="d1f94-166">Te metody zazwyczaj zwróci natychmiast, a operacja może lub nie może faktycznie anulować.</span><span class="sxs-lookup"><span data-stu-id="d1f94-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="d1f94-167">W programie obsługi zdarzeń dla _MethodName_**Complete** zdarzenia _MethodName_**CompleteArgs** obiekt zawiera `Cancelled` pole, które klienci mogą używać do określenia, czy nastąpiło anulowanie.</span><span class="sxs-lookup"><span data-stu-id="d1f94-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="d1f94-168">Przestrzegaj semantyki anulowania opisanej w [najlepszych rozwiązaniach dotyczących implementowania wzorca asynchronicznego opartego na zdarzeniach.](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="d1f94-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="d1f94-169">Opcjonalnie obsługa isbusy właściwość</span><span class="sxs-lookup"><span data-stu-id="d1f94-169">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="d1f94-170">Jeśli klasa nie obsługuje wielu równoczesnych wywołań, `IsBusy` należy rozważyć ujawnienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1f94-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="d1f94-171">Dzięki temu deweloperzy mogą określić, czy _MethodName_**Async** metoda jest uruchomiona bez przechwytywania wyjątek od _MethodName_**Async** metody.</span><span class="sxs-lookup"><span data-stu-id="d1f94-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="d1f94-172">Przestrzegaj `IsBusy` semantyki opisanej w [najlepszych rozwiązaniach dotyczących implementowania wzorca asynchronicznego opartego na zdarzeniach.](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="d1f94-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="d1f94-173">Opcjonalnie zapewnij obsługę raportowania postępów</span><span class="sxs-lookup"><span data-stu-id="d1f94-173">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="d1f94-174">Często pożądane jest, aby operacja asynchroniczna zgłaszała postęp podczas jej działania.</span><span class="sxs-lookup"><span data-stu-id="d1f94-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="d1f94-175">Wzorzec asynchroniczny oparty na zdarzeniach zawiera wskazówki dotyczące tego.</span><span class="sxs-lookup"><span data-stu-id="d1f94-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="d1f94-176">Opcjonalnie zdefiniuj zdarzenie, które ma być wywoływane przez operację asynchroniczną i wywoływane w odpowiednim wątku.</span><span class="sxs-lookup"><span data-stu-id="d1f94-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="d1f94-177">Obiekt <xref:System.ComponentModel.ProgressChangedEventArgs> zawiera wskaźnik postępu wartości całkowitej, który ma wynosić od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="d1f94-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="d1f94-178">Nazwij to zdarzenie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d1f94-178">Name this event as follows:</span></span>

  - <span data-ttu-id="d1f94-179">`ProgressChanged`jeśli klasa ma wiele operacji asynchronicznych (lub oczekuje się, że wzrośnie do uwzględnienia wielu operacji asynchronicznych w przyszłych wersjach);</span><span class="sxs-lookup"><span data-stu-id="d1f94-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="d1f94-180">_MethodName_**ProgressChanged,** jeśli klasa ma jedną operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="d1f94-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="d1f94-181">Ten wybór nazewnictwa paralele, które dla metody anulowania, zgodnie z opisem w opcjonalnie obsługuje anulowanie sekcji.</span><span class="sxs-lookup"><span data-stu-id="d1f94-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="d1f94-182">To zdarzenie powinno <xref:System.ComponentModel.ProgressChangedEventHandler> używać podpisu <xref:System.ComponentModel.ProgressChangedEventArgs> delegata i klasy.</span><span class="sxs-lookup"><span data-stu-id="d1f94-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="d1f94-183">Alternatywnie, jeśli można podać wskaźnik postępu bardziej specyficzne dla domeny (na przykład bajty odczytu i całkowita liczba <xref:System.ComponentModel.ProgressChangedEventArgs>bajtów dla operacji pobierania), należy zdefiniować klasę pochodną .</span><span class="sxs-lookup"><span data-stu-id="d1f94-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="d1f94-184">Należy zauważyć, że `ProgressChanged` istnieje tylko jedno lub _MethodName_**ProgressChanged** zdarzenie dla klasy, niezależnie od liczby metod asynchronicznych, które obsługuje.</span><span class="sxs-lookup"><span data-stu-id="d1f94-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="d1f94-185">Klienci powinni używać `userState` obiektu, który jest przekazywany do _MethodName_**Async** metody do rozróżniania między aktualizacjami postępu na wiele równoczesnych operacji.</span><span class="sxs-lookup"><span data-stu-id="d1f94-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="d1f94-186">Mogą wystąpić sytuacje, w których wiele operacji obsługuje postęp i każdy zwraca inny wskaźnik postępu.</span><span class="sxs-lookup"><span data-stu-id="d1f94-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="d1f94-187">W takim przypadku `ProgressChanged` pojedyncze zdarzenie nie jest odpowiednie i `ProgressChanged` można rozważyć obsługę wielu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d1f94-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="d1f94-188">W takim przypadku należy użyć wzorca nazewnictwa _MethodName_**ProgressChanged** dla każdej metody**Asynchronia** _Nazwa metody._</span><span class="sxs-lookup"><span data-stu-id="d1f94-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="d1f94-189">Przestrzegaj semantyki raportowania postępu opisane [najlepsze rozwiązania dotyczące implementowania wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d1f94-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="d1f94-190">Opcjonalnie zapewnij obsługę zwracania wyników przyrostowych</span><span class="sxs-lookup"><span data-stu-id="d1f94-190">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="d1f94-191">Czasami operacja asynchroniczna może zwracać wyniki przyrostowe przed zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="d1f94-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="d1f94-192">Istnieje wiele opcji, które mogą służyć do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="d1f94-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="d1f94-193">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="d1f94-193">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="d1f94-194">Klasa jednooperacyjna</span><span class="sxs-lookup"><span data-stu-id="d1f94-194">Single-operation Class</span></span>

<span data-ttu-id="d1f94-195">Jeśli klasa obsługuje tylko jedną operację asynchroniczną, a ta operacja jest w stanie zwracać wyniki przyrostowe, a następnie:</span><span class="sxs-lookup"><span data-stu-id="d1f94-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="d1f94-196">Rozszerz <xref:System.ComponentModel.ProgressChangedEventArgs> typ, aby przenosić przyrostowe dane wyników, i zdefiniuj zdarzenie _MethodName_**ProgressChanged** z tymi rozszerzonymi danymi.</span><span class="sxs-lookup"><span data-stu-id="d1f94-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="d1f94-197">Wynieś to _Zdarzenie MethodName_**ProgressChanged,** gdy istnieje wynik przyrostowy do raportu.</span><span class="sxs-lookup"><span data-stu-id="d1f94-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="d1f94-198">To rozwiązanie ma zastosowanie w szczególności do klasy operacji pojedynczej asynchronicznej, ponieważ nie ma problemu z tym samym zdarzeniem występującym w celu zwrócenia wyników przyrostowych na "wszystkie operacje", tak jak robi to zdarzenie _MethodName_**ProgressChanged.**</span><span class="sxs-lookup"><span data-stu-id="d1f94-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="d1f94-199">Klasa wielooperacjawa z jednorodnymi wynikami przyrostowymi</span><span class="sxs-lookup"><span data-stu-id="d1f94-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="d1f94-200">W takim przypadku klasa obsługuje wiele metod asynchronicznych, z których każda może zwracać wyniki przyrostowe, a te wyniki przyrostowe mają ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="d1f94-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="d1f94-201">Postępuj zgodnie z modelem opisanym powyżej <xref:System.EventArgs> dla klas pojedynczej operacji, ponieważ ta sama struktura będzie działać dla wszystkich wyników przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="d1f94-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="d1f94-202">Zdefiniuj `ProgressChanged` zdarzenie zamiast _Zdarzenia MethodName_**ProgressChanged,** ponieważ ma ono zastosowanie do wielu metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d1f94-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="d1f94-203">Klasa wielooperacjawa z heterogenicznymi wynikami przyrostowymi</span><span class="sxs-lookup"><span data-stu-id="d1f94-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="d1f94-204">Jeśli klasa obsługuje wiele metod asynchronicznych, z których każda zwraca inny typ danych, należy:</span><span class="sxs-lookup"><span data-stu-id="d1f94-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="d1f94-205">Oddziel raporty o wynikach przyrostowych od raportów o postępach.</span><span class="sxs-lookup"><span data-stu-id="d1f94-205">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="d1f94-206">Zdefiniuj oddzielne Zdarzenie <xref:System.EventArgs> _MethodName_**ProgressChanged** z odpowiednim dla każdej metody asynchronicznej do obsługi przyrostowych danych wyników tej metody.</span><span class="sxs-lookup"><span data-stu-id="d1f94-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="d1f94-207">Wywołaj ten program obsługi zdarzeń w odpowiednim wątku, zgodnie z opisem w [najlepszych rozwiązań dotyczących implementowania wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d1f94-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="d1f94-208">Obsługa parametrów out i ref w metodach</span><span class="sxs-lookup"><span data-stu-id="d1f94-208">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="d1f94-209">Mimo że `out` korzystanie `ref` z i jest, ogólnie rzecz biorąc, odradzane w .NET Framework, oto reguły, których należy przestrzegać, gdy są obecne:</span><span class="sxs-lookup"><span data-stu-id="d1f94-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="d1f94-210">Biorąc pod uwagę metodę synchroniczną *MethodName:*</span><span class="sxs-lookup"><span data-stu-id="d1f94-210">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="d1f94-211">`out`parametry *do MethodName* nie powinny być częścią _MethodName_**Async**.</span><span class="sxs-lookup"><span data-stu-id="d1f94-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="d1f94-212">Zamiast tego powinny być częścią _MethodName_**CompletedEventArgs** o tej samej nazwie, co jego odpowiednik parametru w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).</span><span class="sxs-lookup"><span data-stu-id="d1f94-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="d1f94-213">`ref`parametry *do MethodName* powinny być wyświetlane jako część _MethodName_**Async**i jako część _MethodName_**CompletedEventArgs** o tej samej nazwie co jego odpowiednik parametru w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).</span><span class="sxs-lookup"><span data-stu-id="d1f94-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="d1f94-214">Na przykład, biorąc pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="d1f94-214">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="d1f94-215">Metoda asynchroniczna <xref:System.ComponentModel.AsyncCompletedEventArgs> i jej klasa będzie wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="d1f94-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d1f94-216">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1f94-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="d1f94-217">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d1f94-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="d1f94-218">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="d1f94-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="d1f94-219">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="d1f94-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="d1f94-220">Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d1f94-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="d1f94-221">Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d1f94-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="d1f94-222">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="d1f94-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
