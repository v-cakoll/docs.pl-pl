---
title: Operacje synchroniczne i asynchroniczne
description: Dowiedz się więcej o implementowaniu i wywoływaniu asynchronicznych operacji usługi. Usługi i klienci WCF mogą korzystać z operacji asynchronicznych na dwóch poziomach aplikacji.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: f52f2613c96c0149c330bb75f80c6738f8d41146
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245923"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="d3573-104">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="d3573-104">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="d3573-105">W tym temacie omówiono implementowanie i wywoływanie asynchronicznych operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d3573-105">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="d3573-106">Wiele aplikacji wywołuje metody asynchronicznie, ponieważ umożliwia aplikacjom kontynuowanie pracy przydatnej podczas wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d3573-106">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="d3573-107">Usługi Windows Communication Foundation (WCF) i klienci mogą uczestniczyć w asynchronicznych wywołaniach operacji na dwóch odrębnych poziomach aplikacji, co zapewnia aplikacjom WCF jeszcze większą elastyczność w celu zmaksymalizowania równowagi przepływności w odniesieniu do współdziałania.</span><span class="sxs-lookup"><span data-stu-id="d3573-107">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="d3573-108">Typy operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="d3573-108">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="d3573-109">Wszystkie kontrakty usługi w programie WCF, niezależnie od typów parametrów i zwracanych wartości, używają atrybutów programu WCF w celu określenia określonego wzorca komunikatów między klientem i usługą.</span><span class="sxs-lookup"><span data-stu-id="d3573-109">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="d3573-110">Funkcja WCF automatycznie kieruje komunikaty przychodzące i wychodzące do odpowiedniej operacji usługi lub uruchamia kod klienta.</span><span class="sxs-lookup"><span data-stu-id="d3573-110">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="d3573-111">Klient posiada tylko kontrakt usługi, który określa wzorzec wymiany komunikatów dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="d3573-111">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="d3573-112">Klienci mogą oferować deweloperom dowolny model programistyczny, który wybiera, tak długo, jak jest przestrzegany wzorzec wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d3573-112">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="d3573-113">Dzięki temu usługi mogą również implementować operacje w dowolny sposób, tak długo, jak jest zaobserwowany określony wzorzec komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d3573-113">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="d3573-114">Niezależność kontraktu usługi z implementacji usługi lub klienta umożliwia następujące formy wykonywania asynchronicznego w aplikacjach WCF:</span><span class="sxs-lookup"><span data-stu-id="d3573-114">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="d3573-115">Klienci mogą asynchronicznie wywoływać operacje żądania/odpowiedzi przy użyciu synchronicznej wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d3573-115">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="d3573-116">Usługi mogą asynchronicznie zaimplementować operację żądania/odpowiedzi przy użyciu synchronicznej wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d3573-116">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="d3573-117">Wymiana komunikatów może być jednokierunkowa niezależnie od implementacji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="d3573-117">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="d3573-118">Sugerowane scenariusze asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="d3573-118">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="d3573-119">Użyj metody asynchronicznej w implementacji operacji usługi, jeśli implementacja usługi operacji powoduje wywołanie blokujące, takie jak wykonywanie operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="d3573-119">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="d3573-120">Gdy jesteś w implementacji operacji asynchronicznej, spróbuj wywołać asynchroniczne operacje i metody, aby w miarę możliwości rozciągnąć asynchroniczną ścieżkę wywołania.</span><span class="sxs-lookup"><span data-stu-id="d3573-120">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="d3573-121">Na przykład Wywołaj a `BeginOperationTwo()` z poziomu `BeginOperationOne()` .</span><span class="sxs-lookup"><span data-stu-id="d3573-121">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="d3573-122">Użycie asynchronicznej metody w kliencie lub wywoływanie aplikacji w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="d3573-122">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="d3573-123">Jeśli wywołujesz operacje z aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="d3573-123">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="d3573-124">(Aby uzyskać więcej informacji na temat takich scenariuszy, zobacz [aplikacje klienckie warstwy środkowej](./feature-details/middle-tier-client-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="d3573-124">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="d3573-125">Jeśli wywołujesz operacje na stronie ASP.NET, używaj stron asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d3573-125">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="d3573-126">Jeśli wywołujesz operacje z dowolnej aplikacji, która jest jednowątkowa, taka jak Windows Forms lub Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d3573-126">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="d3573-127">W przypadku korzystania z asynchronicznego modelu wywoływania opartego na zdarzeniach zdarzenie wynikowe jest zgłaszane w wątku interfejsu użytkownika, co umożliwia dodanie czasu odpowiedzi do aplikacji bez konieczności samodzielnego obsłużenia wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="d3573-127">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="d3573-128">Ogólnie rzecz biorąc, jeśli istnieje wybór między wywołaniem synchronicznym i asynchronicznym, wybierz wywołanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="d3573-128">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="d3573-129">Implementowanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="d3573-129">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="d3573-130">Operacje asynchroniczne można zaimplementować przy użyciu jednej z trzech następujących metod:</span><span class="sxs-lookup"><span data-stu-id="d3573-130">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="d3573-131">Wzorzec asynchroniczny oparty na zadaniach</span><span class="sxs-lookup"><span data-stu-id="d3573-131">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="d3573-132">Wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d3573-132">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="d3573-133">Wzorzec asynchroniczny IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="d3573-133">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="d3573-134">Wzorzec asynchroniczny oparty na zadaniach</span><span class="sxs-lookup"><span data-stu-id="d3573-134">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="d3573-135">Wzorzec asynchroniczny oparty na zadaniach jest preferowanym sposobem implementacji operacji asynchronicznych, ponieważ jest najłatwiejszym i najbardziej prostym do przodu.</span><span class="sxs-lookup"><span data-stu-id="d3573-135">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="d3573-136">Aby użyć tej metody, wystarczy zaimplementować operację usługi i określić zwracany typ zadania \<T> , gdzie T jest typem zwracanym przez operację logiczną.</span><span class="sxs-lookup"><span data-stu-id="d3573-136">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="d3573-137">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d3573-137">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService
{
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)
   {
      return Task<string>.Factory.StartNew(() =>
      {
         return msg;
      });
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="d3573-138">Operacja SampleMethodTaskAsync zwraca zadanie \<string> , ponieważ operacja logiczna zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="d3573-138">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="d3573-139">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [wzorzec asynchroniczny oparty na zadaniach](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="d3573-139">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d3573-140">W przypadku korzystania ze wzorca asynchronicznego opartego na zadaniach T:System.AggregateException może być zgłaszane, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="d3573-140">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="d3573-141">Ten wyjątek może wystąpić w przypadku klienta lub usług</span><span class="sxs-lookup"><span data-stu-id="d3573-141">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="d3573-142">Wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d3573-142">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="d3573-143">Usługa, która obsługuje wzorzec asynchroniczny oparty na zdarzeniach, będzie mieć co najmniej jedną operację o nazwie MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="d3573-143">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="d3573-144">Te metody mogą dublować wersje synchroniczne, które wykonują tę samą operację na bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="d3573-144">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="d3573-145">Klasa może również mieć zdarzenie MethodNameCompleted i może mieć metodę MethodNameAsyncCancel (lub po prostu CancelAsync).</span><span class="sxs-lookup"><span data-stu-id="d3573-145">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="d3573-146">Klient chcący wywołać operację określi procedurę obsługi zdarzeń, która ma być wywoływana po zakończeniu operacji,</span><span class="sxs-lookup"><span data-stu-id="d3573-146">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="d3573-147">Poniższy fragment kodu ilustruje sposób deklarowania operacji asynchronicznych za pomocą wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="d3573-147">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="d3573-148">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zdarzeniach, zobacz [wzorzec asynchroniczny oparty na zdarzeniach](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d3573-148">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="d3573-149">Wzorzec asynchroniczny IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="d3573-149">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="d3573-150">Operację usługi można zaimplementować w sposób asynchroniczny za pomocą wzorca programowania asynchronicznego .NET Framework i oznaczyć `<Begin>` metodę <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwością ustawioną na `true` .</span><span class="sxs-lookup"><span data-stu-id="d3573-150">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="d3573-151">W takim przypadku operacja asynchroniczna jest uwidaczniana w metadanych w tym samym formularzu co operacja synchroniczna: jest uwidaczniana jako jedna operacja z komunikatem żądania i komunikatem skorelowanej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d3573-151">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="d3573-152">Następnie modele programowania klientów mają wybór.</span><span class="sxs-lookup"><span data-stu-id="d3573-152">Client programming models then have a choice.</span></span> <span data-ttu-id="d3573-153">Mogą one reprezentować ten wzorzec jako operację synchroniczną lub asynchronicznie, tak długo, jak w przypadku wywołania usługi do programu Exchange-odpowiedź żądania.</span><span class="sxs-lookup"><span data-stu-id="d3573-153">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="d3573-154">Ogólnie rzecz biorąc, w przypadku asynchronicznego charakteru systemów nie należy podejmować zależności od wątków.</span><span class="sxs-lookup"><span data-stu-id="d3573-154">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="d3573-155">Najbardziej niezawodnym sposobem przekazywania danych do różnych etapów przetwarzania wysyłania operacji jest korzystanie z rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="d3573-155">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="d3573-156">Aby zapoznać się z przykładem, zobacz [How to: implementowanie asynchronicznej operacji usługi](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="d3573-156">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="d3573-157">Aby zdefiniować operację kontraktu `X` wykonywaną asynchronicznie bez względu na to, jak jest wywoływana w aplikacji klienckiej:</span><span class="sxs-lookup"><span data-stu-id="d3573-157">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="d3573-158">Zdefiniuj dwie metody przy użyciu wzorca `BeginOperation` i `EndOperation` .</span><span class="sxs-lookup"><span data-stu-id="d3573-158">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="d3573-159">`BeginOperation`Metoda obejmuje `in` i `ref` Parametry operacji oraz zwraca <xref:System.IAsyncResult> Typ.</span><span class="sxs-lookup"><span data-stu-id="d3573-159">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="d3573-160">`EndOperation`Metoda zawiera parametr, <xref:System.IAsyncResult> `out` a także parametry i `ref` zwraca typ zwracany operacji.</span><span class="sxs-lookup"><span data-stu-id="d3573-160">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="d3573-161">Na przykład zapoznaj się z następującą metodą.</span><span class="sxs-lookup"><span data-stu-id="d3573-161">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="d3573-162">W celu utworzenia operacji asynchronicznej dwie metody:</span><span class="sxs-lookup"><span data-stu-id="d3573-162">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="d3573-163">Ten <xref:System.ServiceModel.OperationContractAttribute> atrybut jest stosowany tylko do `BeginDoWork` metody.</span><span class="sxs-lookup"><span data-stu-id="d3573-163">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="d3573-164">Kontrakt z wynikiem ma jedną operację WSDL o nazwie `DoWork` .</span><span class="sxs-lookup"><span data-stu-id="d3573-164">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="d3573-165">Wywołania asynchroniczne po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="d3573-165">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="d3573-166">Aplikacja kliencka programu WCF może korzystać z jednego z trzech opisanych asynchronicznie modeli wywołujących</span><span class="sxs-lookup"><span data-stu-id="d3573-166">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="d3573-167">W przypadku korzystania z modelu opartego na zadaniach, po prostu wywołaj operację za pomocą słowa kluczowego await, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="d3573-167">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="d3573-168">Użycie wzorca asynchronicznego opartego na zdarzeniach wymaga dodania procedury obsługi zdarzeń do odebrania powiadomienia o odpowiedzi — a zdarzenie powstałe w wątku interfejsu użytkownika jest automatycznie wywoływane.</span><span class="sxs-lookup"><span data-stu-id="d3573-168">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="d3573-169">Aby użyć tej metody, należy określić opcje polecenia **/Async** i **/TCV: Version35** za pomocą [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d3573-169">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="d3573-170">Gdy to zrobisz, Svcutil.exe generuje klasę klienta WCF z infrastrukturą zdarzeń, która umożliwia aplikacji wywołującej zaimplementowanie i przypisanie obsługi zdarzeń w celu otrzymania odpowiedzi i podjęcia odpowiedniej akcji.</span><span class="sxs-lookup"><span data-stu-id="d3573-170">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="d3573-171">Pełny przykład można znaleźć w temacie [How to: calling Service Operations asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="d3573-171">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="d3573-172">Jednak oparty na zdarzeniach model asynchroniczny jest dostępny tylko w .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="d3573-172">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="d3573-173">Ponadto nie jest to obsługiwane nawet w .NET Framework 3,5 w przypadku utworzenia kanału klienta WCF przy użyciu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d3573-173">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d3573-174">W przypadku obiektów kanału klienta WCF należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do wywołania operacji asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="d3573-174">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="d3573-175">Aby użyć tej metody, należy określić opcję polecenia **/Async** za pomocą [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d3573-175">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="d3573-176">Spowoduje to wygenerowanie kontraktu usługi, w którym każda operacja jest modelowana jako `<Begin>` Metoda z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwością ustawioną na `true` i odpowiadającą jej `<End>` metodę.</span><span class="sxs-lookup"><span data-stu-id="d3573-176">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="d3573-177">Aby zapoznać się z kompletnym przykładem <xref:System.ServiceModel.ChannelFactory%601> , zobacz [How to: Call operacje asynchronicznie przy użyciu fabryki kanałów](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="d3573-177">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="d3573-178">W obu przypadkach aplikacje mogą wywoływać operację asynchronicznie nawet wtedy, gdy usługa jest zaimplementowana synchronicznie, w taki sam sposób, w jaki aplikacja może używać tego samego wzorca do wywołania asynchronicznej metody synchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d3573-178">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="d3573-179">Sposób implementacji operacji nie jest znaczący dla klienta; po nadejściu komunikatu odpowiedzi jego zawartość jest wysyłana do asynchronicznej metody> <klienta, `End` a klient pobiera informacje.</span><span class="sxs-lookup"><span data-stu-id="d3573-179">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="d3573-180">Jednokierunkowe wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="d3573-180">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="d3573-181">Można również utworzyć wzorzec wymiany komunikatów asynchronicznych, w którym operacje jednokierunkowe (operacje, dla których <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> `true` nie ma skorelowanej odpowiedzi) mogą być wysyłane w dowolnym kierunku przez klienta lub usługę niezależnie od drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="d3573-181">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="d3573-182">(W ten sposób jest stosowany wzorzec wymiany komunikatów dupleksowych z komunikatami jednokierunkowymi). W takim przypadku kontrakt usługi określa jednokierunkową wymianę komunikatów, którą każda strona może zaimplementować jako wywołania asynchroniczne lub implementacje, lub nie, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d3573-182">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="d3573-183">Ogólnie rzecz biorąc, gdy kontrakt jest wymianą komunikatów jednokierunkowych, implementacje mogą być w znacznym stopniu asynchroniczne, ponieważ po wysłaniu wiadomości aplikacja nie czeka na odpowiedź i może kontynuować wykonywanie innych czynności.</span><span class="sxs-lookup"><span data-stu-id="d3573-183">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="d3573-184">Klientów asynchronicznych opartych na zdarzeniach i kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="d3573-184">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="d3573-185">Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana jako `Result` Właściwość, a pozostałe są zwracane jako właściwości w <xref:System.EventArgs> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="d3573-185">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="d3573-186">W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość jako `Result` Właściwość, a reszta jest właściwościami <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3573-186">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="d3573-187">Jeśli chcesz otrzymać obiekt komunikatu jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, użyj opcji polecenia **/MessageContract** .</span><span class="sxs-lookup"><span data-stu-id="d3573-187">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="d3573-188">Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3573-188">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="d3573-189">Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d3573-189">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3573-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3573-190">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
