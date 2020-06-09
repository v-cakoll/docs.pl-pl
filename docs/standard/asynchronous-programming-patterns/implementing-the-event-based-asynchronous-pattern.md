---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
description: Dowiedz się, jak zaimplementować wzorzec asynchroniczny oparty na zdarzeniach (EAP) w programie .NET. Protokół EAP jest standardowym sposobem spakowania klasy, która ma funkcje asynchroniczne.
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
ms.openlocfilehash: 9ffb2e2f426e2d2d97998a89a3e8d306de4f29ca
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583664"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f1722-104">Implementacja wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f1722-104">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="f1722-105">W przypadku pisania klasy z niektórymi operacjami, które mogą mieć zauważalne opóźnienia, należy rozważyć udzielenie funkcji asynchronicznych przez implementację [asynchronicznego wzorca opartego na zdarzeniach](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-105">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="f1722-106">Wzorzec asynchroniczny oparty na zdarzeniach zapewnia ustandaryzowany sposób spakowania klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="f1722-106">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="f1722-107">Jeśli zaimplementowano klasy pomocnika, takie jak <xref:System.ComponentModel.AsyncOperationManager> , Klasa będzie działała prawidłowo w ramach dowolnego modelu aplikacji, w tym ASP.NET, aplikacji konsolowych i aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f1722-107">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="f1722-108">Aby zapoznać się z przykładem, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [How to: Implementuj składnik, który obsługuje wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-108">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="f1722-109">W przypadku prostych operacji asynchronicznych można znaleźć <xref:System.ComponentModel.BackgroundWorker> odpowiedni składnik.</span><span class="sxs-lookup"><span data-stu-id="f1722-109">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="f1722-110">Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker> , zobacz [jak: uruchamianie operacji w tle](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-110">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="f1722-111">Na poniższej liście opisano funkcje wzorca asynchronicznego opartego na zdarzeniach omówione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f1722-111">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="f1722-112">Możliwości implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f1722-112">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="f1722-113">Nazewnictwo metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="f1722-113">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="f1722-114">Opcjonalna obsługa anulowania</span><span class="sxs-lookup"><span data-stu-id="f1722-114">Optionally Support Cancellation</span></span>

- <span data-ttu-id="f1722-115">Opcjonalnie można obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="f1722-115">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="f1722-116">Opcjonalnie zapewniaj obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="f1722-116">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="f1722-117">Opcjonalnie zapewnić obsługę zwracania wyników przyrostowych</span><span class="sxs-lookup"><span data-stu-id="f1722-117">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="f1722-118">Obsługa parametrów out i ref w metodach</span><span class="sxs-lookup"><span data-stu-id="f1722-118">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f1722-119">Możliwości implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f1722-119">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="f1722-120">Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach, gdy:</span><span class="sxs-lookup"><span data-stu-id="f1722-120">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="f1722-121">Klienci klasy nie potrzebują <xref:System.Threading.WaitHandle> i są <xref:System.IAsyncResult> obiektami dostępnymi dla operacji asynchronicznych, co oznacza, że sondowanie i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> wymagane jest skompilowanie przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f1722-121">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="f1722-122">Chcesz, aby operacje asynchroniczne były zarządzane przez klienta z modelem znanego zdarzenia/delegata.</span><span class="sxs-lookup"><span data-stu-id="f1722-122">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="f1722-123">Każda operacja jest kandydatem do implementacji asynchronicznej, ale powinny być brane pod uwagę długie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="f1722-123">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="f1722-124">Szczególnie odpowiednie są operacje, w których klienci wywołujący metodę i są powiadamiani o zakończeniu, bez konieczności dalszej interwencji.</span><span class="sxs-lookup"><span data-stu-id="f1722-124">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="f1722-125">Odpowiednie są również operacje, które działają w sposób ciągły, przez okresowe powiadamianie klientów o postępie, wyniki przyrostowe lub zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="f1722-125">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="f1722-126">Aby uzyskać więcej informacji na temat decydowania, kiedy obsługiwać wzorzec asynchroniczny oparty na zdarzeniach, zobacz [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-126">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="f1722-127">Nazewnictwo metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="f1722-127">Naming Asynchronous Methods</span></span>

<span data-ttu-id="f1722-128">Dla każdej metody synchronicznej *MethodName* , dla której chcesz dostarczyć odpowiednik asynchroniczny:</span><span class="sxs-lookup"><span data-stu-id="f1722-128">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="f1722-129">Zdefiniuj metodę _MethodName_**asynchroniczną** MethodName, która:</span><span class="sxs-lookup"><span data-stu-id="f1722-129">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="f1722-130">Zwraca wartość `void`.</span><span class="sxs-lookup"><span data-stu-id="f1722-130">Returns `void`.</span></span>

- <span data-ttu-id="f1722-131">Przyjmuje te same parametry co Metoda *MethodName* .</span><span class="sxs-lookup"><span data-stu-id="f1722-131">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="f1722-132">Akceptuje wiele wywołań.</span><span class="sxs-lookup"><span data-stu-id="f1722-132">Accepts multiple invocations.</span></span>

<span data-ttu-id="f1722-133">Opcjonalnie można zdefiniować Przeciążenie**Async** _MethodName_, identyczne z _MethodName_**Async**, ale z dodatkowym parametrem zwracającym obiekt `userState` .</span><span class="sxs-lookup"><span data-stu-id="f1722-133">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="f1722-134">Zrób to, jeśli przygotowano się do zarządzania wieloma współbieżnymi wywołaniami metody, w tym przypadku `userState` wartość zostanie dostarczona do wszystkich programów obsługi zdarzeń w celu odróżnienia wywołań metody.</span><span class="sxs-lookup"><span data-stu-id="f1722-134">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="f1722-135">Możesz również wybrać tę opcję po prostu w miejscu przechowywania stanu użytkownika w celu późniejszego pobrania.</span><span class="sxs-lookup"><span data-stu-id="f1722-135">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="f1722-136">Dla każdej oddzielnej sygnatury metody**asynchronicznej** _MethodName_:</span><span class="sxs-lookup"><span data-stu-id="f1722-136">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="f1722-137">Zdefiniuj następujące zdarzenie w tej samej klasie co Metoda:</span><span class="sxs-lookup"><span data-stu-id="f1722-137">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="f1722-138">Zdefiniuj następujących delegatów i <xref:System.ComponentModel.AsyncCompletedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="f1722-138">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="f1722-139">Prawdopodobnie zostaną one zdefiniowane poza klasą, ale w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1722-139">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="f1722-140">Upewnij się, że Klasa _MethodName_**CompletedEventArgs** uwidacznia jej składowe jako właściwości tylko do odczytu, a nie pola, jako że pola uniemożliwiają powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="f1722-140">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="f1722-141">Nie należy definiować <xref:System.ComponentModel.AsyncCompletedEventArgs> klas pochodnych dla metod, które nie generują wyników.</span><span class="sxs-lookup"><span data-stu-id="f1722-141">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="f1722-142">Wystarczy użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> samego siebie.</span><span class="sxs-lookup"><span data-stu-id="f1722-142">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="f1722-143">Jest to doskonale akceptowalne, gdy jest to możliwe i odpowiednie, aby ponownie użyć delegatów i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów.</span><span class="sxs-lookup"><span data-stu-id="f1722-143">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="f1722-144">W takim przypadku nazewnictwo nie będzie zgodne z nazwą metody, ponieważ dany delegat i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie zostanie powiązany z pojedynczą metodą.</span><span class="sxs-lookup"><span data-stu-id="f1722-144">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="f1722-145">Opcjonalna obsługa anulowania</span><span class="sxs-lookup"><span data-stu-id="f1722-145">Optionally Support Cancellation</span></span>

<span data-ttu-id="f1722-146">Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, anulowanie powinno być uwidocznione na kliencie zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="f1722-146">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="f1722-147">Należy pamiętać, że przed zdefiniowaniem pomocy technicznej dotyczącej anulowania należy wziąć pod uwagę dwa punkty decyzyjne:</span><span class="sxs-lookup"><span data-stu-id="f1722-147">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="f1722-148">Czy Klasa, wraz z przyszłymi zaplanowanymi do niej dodatkami, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?</span><span class="sxs-lookup"><span data-stu-id="f1722-148">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="f1722-149">Czy operacje asynchroniczne obsługujące anulowanie obsługują wiele oczekujących operacji?</span><span class="sxs-lookup"><span data-stu-id="f1722-149">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="f1722-150">Oznacza to, że metoda _MethodName_**Async** MethodName przyjmuje `userState` parametr i zezwala na wielokrotne wywołania przed oczekiwaniem na zakończenie?</span><span class="sxs-lookup"><span data-stu-id="f1722-150">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="f1722-151">Użyj odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, co ma być sygnaturą dla metody anulowania.</span><span class="sxs-lookup"><span data-stu-id="f1722-151">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="f1722-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1722-152">Visual Basic</span></span>

||<span data-ttu-id="f1722-153">Obsługiwane są liczne operacje jednoczesne</span><span class="sxs-lookup"><span data-stu-id="f1722-153">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="f1722-154">Tylko jedna operacja w danym momencie</span><span class="sxs-lookup"><span data-stu-id="f1722-154">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="f1722-155">Jedna operacja asynchroniczna w całej klasie</span><span class="sxs-lookup"><span data-stu-id="f1722-155">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="f1722-156">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="f1722-156">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="f1722-157">C\#</span><span class="sxs-lookup"><span data-stu-id="f1722-157">C\#</span></span>

||<span data-ttu-id="f1722-158">Obsługiwane są liczne operacje jednoczesne</span><span class="sxs-lookup"><span data-stu-id="f1722-158">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="f1722-159">Tylko jedna operacja w danym momencie</span><span class="sxs-lookup"><span data-stu-id="f1722-159">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="f1722-160">Jedna operacja asynchroniczna w całej klasie</span><span class="sxs-lookup"><span data-stu-id="f1722-160">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="f1722-161">Wiele operacji asynchronicznych w klasie</span><span class="sxs-lookup"><span data-stu-id="f1722-161">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="f1722-162">W przypadku zdefiniowania `CancelAsync(object userState)` metody należy zachować ostrożność podczas wybierania ich wartości stanu, aby umożliwić im odróżnienie między wszystkimi metodami asynchronicznymi wywoływanymi na obiekcie, a nie tylko między wszystkimi wywołaniami pojedynczej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="f1722-162">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="f1722-163">Decyzja o nazwie pojedynczej operacji asynchronicznej w wersji _MethodName_**AsyncCancel** opiera się na umożliwieniu łatwiejszej odnajdywania metody w środowisku projektowym, takim jak funkcja IntelliSense programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1722-163">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="f1722-164">Ta grupa pokrewnych członków i odróżnia je od innych członków, którzy nie mają nic do wykonania z funkcjami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="f1722-164">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="f1722-165">Jeśli spodziewasz się, że w kolejnych wersjach można dodać dodatkowe operacje asynchroniczne, lepiej jest zdefiniować `CancelAsync` .</span><span class="sxs-lookup"><span data-stu-id="f1722-165">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="f1722-166">Nie należy definiować wielu metod z tabeli powyżej w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="f1722-166">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="f1722-167">To nie ma sensu lub będzie zasłaniać interfejs klasy z proliferacją metod.</span><span class="sxs-lookup"><span data-stu-id="f1722-167">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="f1722-168">Te metody zwykle zwracają natychmiast, a operacja może być w rzeczywistości niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="f1722-168">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="f1722-169">W obsłudze zdarzeń dla zdarzenia _MethodName_**ukończone** , obiekt _MethodName_**CompletedEventArgs** zawiera `Cancelled` pole, którego klienci mogą użyć do określenia, czy wystąpiło anulowanie.</span><span class="sxs-lookup"><span data-stu-id="f1722-169">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="f1722-170">Przestrzegaj semantyki anulowania opisanej w [najlepszych rozwiązaniach dotyczących implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-170">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="f1722-171">Opcjonalnie można obsługiwać Właściwość IsBusy</span><span class="sxs-lookup"><span data-stu-id="f1722-171">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="f1722-172">Jeśli Klasa nie obsługuje wielu współbieżnych wywołań, rozważ uwidocznienie `IsBusy` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1722-172">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="f1722-173">Dzięki temu deweloperzy mogą określić, czy metoda**Async** _MethodName_jest uruchomiona bez przechwycenia wyjątku z metody _MethodName_**asynchronicznej** MethodName.</span><span class="sxs-lookup"><span data-stu-id="f1722-173">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="f1722-174">Przestrzegaj `IsBusy` semantyki opisanej w [najlepszych rozwiązaniach dotyczących implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-174">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="f1722-175">Opcjonalnie zapewniaj obsługę raportowania postępu</span><span class="sxs-lookup"><span data-stu-id="f1722-175">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="f1722-176">Jest on często pożądany w przypadku operacji asynchronicznej do raportowania postępu w trakcie jego działania.</span><span class="sxs-lookup"><span data-stu-id="f1722-176">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="f1722-177">Wzorzec asynchroniczny oparty na zdarzeniach zawiera wytyczne umożliwiające wykonanie tej czynności.</span><span class="sxs-lookup"><span data-stu-id="f1722-177">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="f1722-178">Opcjonalnie zdefiniuj zdarzenie, które ma zostać wywołane przez operację asynchroniczną i wywołane w odpowiednim wątku.</span><span class="sxs-lookup"><span data-stu-id="f1722-178">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="f1722-179"><xref:System.ComponentModel.ProgressChangedEventArgs>Obiekt ma wskaźnik postępu o wartościach całkowitych, który powinien mieć wartość z przedziału od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="f1722-179">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="f1722-180">Nazwij to zdarzenie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f1722-180">Name this event as follows:</span></span>

  - <span data-ttu-id="f1722-181">`ProgressChanged`Jeśli klasa ma wiele operacji asynchronicznych (lub można ją zwiększyć, aby uwzględnić wiele operacji asynchronicznych w przyszłych wersjach);</span><span class="sxs-lookup"><span data-stu-id="f1722-181">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="f1722-182">_MethodName_**ProgressChanged** , jeśli klasa ma pojedynczą operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="f1722-182">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="f1722-183">To wybór nazywa się równoległą, która została wprowadzona dla metody anulowania, zgodnie z opisem w sekcji anulowanie pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="f1722-183">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="f1722-184">To zdarzenie powinno używać <xref:System.ComponentModel.ProgressChangedEventHandler> podpisu delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="f1722-184">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="f1722-185">Alternatywnie, jeśli można podać bardziej szczegółowy wskaźnik postępu dla domeny (na przykład odczytane bajty i całkowita liczba bajtów dla operacji pobierania), należy zdefiniować klasę pochodną <xref:System.ComponentModel.ProgressChangedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="f1722-185">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="f1722-186">Należy zauważyć, że dla klasy istnieje tylko jedno `ProgressChanged` lub _MethodName_zdarzenie**ProgressChanged** , niezależnie od liczby obsługiwanych przez nią metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="f1722-186">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="f1722-187">Klienci powinni używać `userState` obiektu, który jest przesyłany do metod**asynchronicznych** _MethodName_, aby rozróżnić aktualizacje postępu dla wielu współbieżnych operacji.</span><span class="sxs-lookup"><span data-stu-id="f1722-187">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="f1722-188">Mogą wystąpić sytuacje, w których wiele operacji obsługuje postęp, a każdy z nich zwraca inny wskaźnik na potrzeby postępu.</span><span class="sxs-lookup"><span data-stu-id="f1722-188">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="f1722-189">W takim przypadku pojedyncze `ProgressChanged` zdarzenie nie jest odpowiednie i można rozważyć obsługę wielu `ProgressChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f1722-189">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="f1722-190">W takim przypadku należy użyć wzorca nazewnictwa _MethodName_**ProgressChanged** dla każdej metody**asynchronicznej** _MethodName_.</span><span class="sxs-lookup"><span data-stu-id="f1722-190">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="f1722-191">Przestrzegaj analizy postępu — opisane są [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-191">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="f1722-192">Opcjonalnie zapewnić obsługę zwracania wyników przyrostowych</span><span class="sxs-lookup"><span data-stu-id="f1722-192">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="f1722-193">Czasami operacja asynchroniczna może zwrócić przyrostowe wyniki przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="f1722-193">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="f1722-194">Istnieje kilka opcji, których można użyć do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f1722-194">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="f1722-195">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="f1722-195">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="f1722-196">Klasa jednooperacji</span><span class="sxs-lookup"><span data-stu-id="f1722-196">Single-operation Class</span></span>

<span data-ttu-id="f1722-197">Jeśli klasa obsługuje tylko pojedynczą operację asynchroniczną, a ta operacja może zwracać wyniki przyrostowe, wówczas:</span><span class="sxs-lookup"><span data-stu-id="f1722-197">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="f1722-198">Rozszerzaj <xref:System.ComponentModel.ProgressChangedEventArgs> Typ, aby przenieść przyrostowe dane wynikowe, i zdefiniuj zdarzenie _MethodName_**ProgressChanged** z tymi rozszerzonymi danymi.</span><span class="sxs-lookup"><span data-stu-id="f1722-198">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="f1722-199">Zgłoś to zdarzenie _MethodName_**ProgressChanged** , gdy istnieje przyrostowy wynik do raportowania.</span><span class="sxs-lookup"><span data-stu-id="f1722-199">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="f1722-200">To rozwiązanie dotyczy w odróżnieniu od klasy operacji pojedynczej asynchronicznej, ponieważ nie występuje problem z tym samym zdarzeniem, które ma zwrócić przyrostowe wyniki na "wszystkie operacje", ponieważ zdarzenie _MethodName_**ProgressChanged** .</span><span class="sxs-lookup"><span data-stu-id="f1722-200">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="f1722-201">Klasa wielu operacji ze jednorodnymi wynikami przyrostowymi</span><span class="sxs-lookup"><span data-stu-id="f1722-201">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="f1722-202">W takim przypadku Klasa obsługuje wiele metod asynchronicznych, z których każda może zwracać wyniki przyrostowe, a wszystkie te same wyniki mają ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="f1722-202">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="f1722-203">Postępuj zgodnie z modelem opisanym powyżej dla klas jednooperacji, ponieważ ta sama <xref:System.EventArgs> Struktura będzie działała dla wszystkich wyników przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="f1722-203">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="f1722-204">Zdefiniuj `ProgressChanged` zdarzenie zamiast zdarzenia _MethodName_**ProgressChanged** , ponieważ ma zastosowanie do wielu metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="f1722-204">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="f1722-205">Klasa wielu operacji z niejednorodnymi wynikami przyrostowymi</span><span class="sxs-lookup"><span data-stu-id="f1722-205">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="f1722-206">Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwraca inny typ danych, należy:</span><span class="sxs-lookup"><span data-stu-id="f1722-206">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="f1722-207">Oddziel raportowanie wyników przyrostowych od raportów postępu.</span><span class="sxs-lookup"><span data-stu-id="f1722-207">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="f1722-208">Zdefiniuj oddzielne zdarzenie _MethodName_**ProgressChanged** z odpowiednimi <xref:System.EventArgs> dla każdej metody asynchronicznej do obsługi danych przyrostowych wyniku tej metody.</span><span class="sxs-lookup"><span data-stu-id="f1722-208">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="f1722-209">Wywołaj ten program obsługi zdarzeń w odpowiednim wątku zgodnie z opisem w [temacie najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f1722-209">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="f1722-210">Obsługa parametrów out i ref w metodach</span><span class="sxs-lookup"><span data-stu-id="f1722-210">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="f1722-211">Chociaż korzystanie z `out` i `ref` jest ogólnie zalecane w .NET Framework, poniżej przedstawiono reguły, które należy wykonać, gdy są obecne:</span><span class="sxs-lookup"><span data-stu-id="f1722-211">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="f1722-212">Nadana metoda synchroniczna *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="f1722-212">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="f1722-213">`out`parametry do *MethodName* nie powinny być częścią _MethodName_**Async**.</span><span class="sxs-lookup"><span data-stu-id="f1722-213">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="f1722-214">Zamiast tego powinny one być częścią _MethodName_**CompletedEventArgs** o tej samej nazwie, co odpowiedni parametr w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).</span><span class="sxs-lookup"><span data-stu-id="f1722-214">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="f1722-215">`ref`parametry do *MethodName* powinny być wyświetlane jako część _MethodName_**Async**MethodName, a jako część CompletedEventArgs _MethodName_**CompletedEventArgs** o takiej samej nazwie jak jej parametr odpowiedni w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).</span><span class="sxs-lookup"><span data-stu-id="f1722-215">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="f1722-216">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f1722-216">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="f1722-217">Metoda asynchroniczna i jej <xref:System.ComponentModel.AsyncCompletedEventArgs> Klasa będą wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f1722-217">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f1722-218">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1722-218">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="f1722-219">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f1722-219">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="f1722-220">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="f1722-220">How to: Run an Operation in the Background</span></span>](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="f1722-221">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="f1722-221">How to: Implement a Form That Uses a Background Operation</span></span>](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="f1722-222">Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f1722-222">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="f1722-223">Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f1722-223">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="f1722-224">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="f1722-224">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
