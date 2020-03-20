---
title: Operacje synchroniczne i asynchroniczne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143216"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="220d3-102">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="220d3-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="220d3-103">W tym temacie omówiono implementowanie i wywoływanie operacji usługi asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="220d3-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="220d3-104">Wiele aplikacji wywołać metody asynchronicznie, ponieważ umożliwia aplikacji, aby kontynuować wykonywanie przydatnej pracy podczas wykonywania wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="220d3-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="220d3-105">Usługi i klienci Windows Communication Foundation (WCF) mogą uczestniczyć w asynchronicznym wywołaniach operacyjnych na dwóch różnych poziomach aplikacji, które zapewniają aplikacjom WCF jeszcze większą elastyczność, aby zmaksymalizować przepustowość zrównoważoną względem interaktywności .</span><span class="sxs-lookup"><span data-stu-id="220d3-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="220d3-106">Rodzaje operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="220d3-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="220d3-107">Wszystkie kontrakty serwisowe w WCF, bez względu na typy parametrów i wartości zwracane, użyj atrybutów WCF, aby określić wzorzec wymiany określonego komunikatu między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="220d3-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="220d3-108">WCF automatycznie kieruje przychodzące i wychodzące wiadomości do odpowiedniej operacji usługi lub uruchomionego kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="220d3-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="220d3-109">Klient posiada tylko umowy serwisowej, która określa wzorzec wymiany komunikatów dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="220d3-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="220d3-110">Klienci mogą zaoferować deweloperowi dowolny model programowania, który wybierze, o ile zostanie zaobserwowany wzorzec wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="220d3-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="220d3-111">Tak też można zaimplementować operacje w dowolny sposób, tak długo, jak określony wzorzec komunikatów jest przestrzegane.</span><span class="sxs-lookup"><span data-stu-id="220d3-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="220d3-112">Niezależność umowy serwisowej od implementacji usługi lub klienta umożliwia następujące formy wykonywania asynchronicznego w aplikacjach WCF:</span><span class="sxs-lookup"><span data-stu-id="220d3-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="220d3-113">Klienci mogą wywoływać operacje żądania/odpowiedzi asynchronicznie przy użyciu synchronicznie wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="220d3-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="220d3-114">Usługi można zaimplementować operację żądania/odpowiedzi asynchronicznie przy użyciu synchronicznie wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="220d3-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="220d3-115">Wymiana komunikatów może być jednokierunkowa, niezależnie od implementacji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="220d3-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="220d3-116">Sugerowane scenariusze asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="220d3-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="220d3-117">Użyj podejścia asynchroniiowego w implementacji operacji usługi, jeśli implementacja usługi operacji wywołuje blokowanie, takie jak wykonywanie pracy we/wy.</span><span class="sxs-lookup"><span data-stu-id="220d3-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="220d3-118">Gdy jesteś w implementacji operacji asynchroniiowej, spróbuj wywołać operacje asynchroniczne i metody, aby rozszerzyć ścieżkę wywołania asynchroniiowego tak daleko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="220d3-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="220d3-119">Na przykład wywołać `BeginOperationTwo()` `BeginOperationOne()`od wewnątrz .</span><span class="sxs-lookup"><span data-stu-id="220d3-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="220d3-120">Użyj podejścia asynchroniiowego w aplikacji klienta lub wywołującej w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="220d3-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="220d3-121">Jeśli wywołujesz operacje z aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="220d3-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="220d3-122">(Aby uzyskać więcej informacji na temat takich scenariuszy, zobacz [Aplikacje klienckie warstwy środkowej](./feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="220d3-122">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="220d3-123">Jeśli wywołujesz operacje w ASP.NET stronie, użyj stron asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="220d3-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="220d3-124">Jeśli wywołujesz operacje z dowolnej aplikacji, która jest jednowątkowa, takich jak Windows Forms lub Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="220d3-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="220d3-125">Podczas korzystania z modelu wywoływania asynchronicznego opartego na zdarzeniach zdarzenie wynik jest wywoływane w wątku interfejsu użytkownika, dodając responsywność do aplikacji bez konieczności obsługi wielu wątków samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="220d3-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="220d3-126">Ogólnie rzecz biorąc, jeśli masz wybór między wywołaniem synchroniowym i asynchronialnym, wybierz wywołanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="220d3-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="220d3-127">Implementowanie operacji usługi asynchroniiowej</span><span class="sxs-lookup"><span data-stu-id="220d3-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="220d3-128">Operacje asynchroniczne można zaimplementować przy użyciu jednej z trzech następujących metod:</span><span class="sxs-lookup"><span data-stu-id="220d3-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="220d3-129">Wzorzec asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="220d3-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="220d3-130">Wzorzec asynchroniczne oparte na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="220d3-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="220d3-131">Wzór asynchroniczne IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="220d3-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="220d3-132">Wzorzec asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="220d3-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="220d3-133">Wzorzec asynchroniczne oparte na zadaniach jest preferowanym sposobem implementowania operacji asynchronicznych, ponieważ jest najprostszym i najbardziej prostym.</span><span class="sxs-lookup"><span data-stu-id="220d3-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="220d3-134">Aby użyć tej metody wystarczy zaimplementować\<operację usługi i określić typ zwracany zadania T>, gdzie T jest typem zwróconym przez operację logiczną.</span><span class="sxs-lookup"><span data-stu-id="220d3-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="220d3-135">Przykład:</span><span class="sxs-lookup"><span data-stu-id="220d3-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="220d3-136">Operacja SampleMethodTaskAsync zwraca\<ciąg zadań> ponieważ operacja logiczna zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="220d3-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="220d3-137">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [Wzorzec asynchroniczne oparte na zadaniach](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="220d3-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="220d3-138">Podczas korzystania z wzorca asynchronicznego opartego na zadaniach może zostać zgłoszony, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="220d3-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="220d3-139">Wyjątek ten może wystąpić w przypadku klienta lub usług</span><span class="sxs-lookup"><span data-stu-id="220d3-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="220d3-140">Wzorzec asynchroniczne oparte na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="220d3-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="220d3-141">Usługa, która obsługuje wzorzec asynchroniczne oparte na zdarzenia będzie miał jedną lub więcej operacji o nazwie MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="220d3-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="220d3-142">Metody te mogą dublować wersje synchroniczne, które wykonują tę samą operację w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="220d3-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="220d3-143">Klasa może również mieć MethodNameCompleted zdarzenia i może mieć MethodNameAsyncCancel (lub po prostu CancelAsync) metoda.</span><span class="sxs-lookup"><span data-stu-id="220d3-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="220d3-144">Klient, który chce wywołać operację, zdefiniuje program obsługi zdarzeń, który ma zostać wywołany po zakończeniu operacji,</span><span class="sxs-lookup"><span data-stu-id="220d3-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="220d3-145">Poniższy fragment kodu ilustruje sposób deklarowania operacji asynchronicznych przy użyciu wzorca asynchronitycznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="220d3-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="220d3-146">Aby uzyskać więcej informacji na temat wzorca asynchroniowego opartego na zdarzeniach, zobacz [Wzorzec asynchroniczne oparte na zdarzeniach](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="220d3-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="220d3-147">Wzór asynchroniczne IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="220d3-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="220d3-148">Operację usługi można zaimplementować w sposób asynchroniczne przy użyciu wzorca programowania `<Begin>` asynchronitycznego `true`programu .NET Framework i oznaczania metody z właściwością ustawioną na <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> .</span><span class="sxs-lookup"><span data-stu-id="220d3-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="220d3-149">W takim przypadku operacja asynchroniza jest widoczna w metadanych w tej samej formie co operacja synchroniczni: jest widoczna jako pojedyncza operacja z komunikatem żądania i komunikatem skorelowanej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="220d3-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="220d3-150">Modele programowania klienta mają wtedy wybór.</span><span class="sxs-lookup"><span data-stu-id="220d3-150">Client programming models then have a choice.</span></span> <span data-ttu-id="220d3-151">Mogą reprezentować ten wzorzec jako operację synchronicznie lub jako operację asynchronizacyjną, o ile po wywołaniu usługi odbywa się wymiana komunikatów żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="220d3-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="220d3-152">Ogólnie rzecz biorąc, z asynchronialnego charakteru systemów, nie należy przyjmować zależności od wątków.</span><span class="sxs-lookup"><span data-stu-id="220d3-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="220d3-153">Najbardziej niezawodnym sposobem przekazywania danych na różnych etapach przetwarzania wysyłki operacji jest użycie rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="220d3-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="220d3-154">Na przykład zobacz [Jak: Implementowanie operacji usługi asynchroniiowej](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="220d3-154">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="220d3-155">Aby zdefiniować `X` operację kontraktu, która jest wykonywana asynchronicznie, niezależnie od tego, jak jest wywoływana w aplikacji klienckiej:</span><span class="sxs-lookup"><span data-stu-id="220d3-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="220d3-156">Zdefiniuj `BeginOperation` dwie `EndOperation`metody za pomocą wzorca i .</span><span class="sxs-lookup"><span data-stu-id="220d3-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="220d3-157">Metoda `BeginOperation` zawiera `in` `ref` i parametry dla operacji <xref:System.IAsyncResult> i zwraca typ.</span><span class="sxs-lookup"><span data-stu-id="220d3-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="220d3-158">Metoda `EndOperation` zawiera <xref:System.IAsyncResult> parametr, a `out` także `ref` parametry i zwraca typ zwracany operacje.</span><span class="sxs-lookup"><span data-stu-id="220d3-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="220d3-159">Na przykład zobacz następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="220d3-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="220d3-160">Aby utworzyć operację asynchronizacyjną, dwie metody będą następujące:</span><span class="sxs-lookup"><span data-stu-id="220d3-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
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
> <span data-ttu-id="220d3-161">Atrybut <xref:System.ServiceModel.OperationContractAttribute> jest stosowany tylko do `BeginDoWork` metody.</span><span class="sxs-lookup"><span data-stu-id="220d3-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="220d3-162">Wynikowy kontrakt ma jedną operację `DoWork`WSDL o nazwie .</span><span class="sxs-lookup"><span data-stu-id="220d3-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="220d3-163">Wywołania asynchroniczne po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="220d3-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="220d3-164">Aplikacja kliencka WCF może używać dowolnego z trzech asynchronicznych modeli wywołujących opisanych wcześniej</span><span class="sxs-lookup"><span data-stu-id="220d3-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="220d3-165">Podczas korzystania z modelu opartego na zadaniach wystarczy wywołać operację przy użyciu await słowa kluczowego, jak pokazano w poniższym fragmentie kodu.</span><span class="sxs-lookup"><span data-stu-id="220d3-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="220d3-166">Przy użyciu wzorca asynchroniiowego oparte na zdarzeniach wymaga tylko dodanie programu obsługi zdarzeń, aby otrzymać powiadomienie o odpowiedzi - i wynikowe zdarzenie jest wywoływane w wątku interfejsu użytkownika automatycznie.</span><span class="sxs-lookup"><span data-stu-id="220d3-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="220d3-167">Aby użyć tego podejścia, należy określić opcje polecenia **/async** i **/tcv:Version35** za pomocą [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="220d3-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="220d3-168">Po wykonaniu tej czynności Svcutil.exe generuje klasę klienta WCF z infrastrukturą zdarzeń, która umożliwia aplikacji wywołującej do zaimplementowania i przypisać program obsługi zdarzeń, aby otrzymać odpowiedź i podjąć odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="220d3-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="220d3-169">Aby uzyskać pełny przykład, zobacz [Jak: Wywołanie operacji usługi Asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="220d3-169">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="220d3-170">Model asynchroniczne oparty na zdarzeniach jest jednak dostępny tylko w programach .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="220d3-170">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="220d3-171">Ponadto nie jest obsługiwany nawet w .NET Framework 3.5, gdy kanał klienta <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>WCF jest tworzony przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="220d3-171">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="220d3-172">Z WCF obiektów kanału klienta, należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do wywoływania operacji asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="220d3-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="220d3-173">Aby użyć tego podejścia, należy określić **/async** opcji polecenia z [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="220d3-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="220d3-174">Generuje umowy serwisowej, w którym każda `<Begin>` operacja jest <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> modelowany `true` jako `<End>` metoda z właściwości ustawionej i odpowiedniej metody.</span><span class="sxs-lookup"><span data-stu-id="220d3-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="220d3-175">Pełny przykład przy <xref:System.ServiceModel.ChannelFactory%601>użyciu , zobacz [Jak: Wywołanie operacji asynchronicznie przy użyciu fabryki kanałów](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="220d3-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="220d3-176">W obu przypadkach aplikacje mogą wywoływać operację asynchronicznie, nawet jeśli usługa jest implementowana synchronicznie, w taki sam sposób, w jaki aplikacja może używać tego samego wzorca do wywoływania asynchronicznie lokalnej metody synchroniczowej.</span><span class="sxs-lookup"><span data-stu-id="220d3-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="220d3-177">Sposób implementacji operacji nie ma znaczenia dla klienta; po odebraniu komunikatu odpowiedzi jego zawartość jest wywoływana do asynchroniczne <`End`> metody klienta i klient pobiera informacje.</span><span class="sxs-lookup"><span data-stu-id="220d3-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="220d3-178">Wzorce wymiany komunikatów jednokierunkowych</span><span class="sxs-lookup"><span data-stu-id="220d3-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="220d3-179">Można również utworzyć wzorzec wymiany komunikatów asynchronicznych, w <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> którym `true` operacje jednokierunkowe (operacje, dla których jest nie ma skorelowanej odpowiedzi) mogą być wysyłane w kierunku przez klienta lub usługi niezależnie od drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="220d3-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="220d3-180">(Spowoduje to użycie wzorca wymiany komunikatów dupleksu z komunikatami jednokierunkowymi). W takim przypadku umowa serwisowa określa jednokierunkową wymianę komunikatów, która każda ze stron może zaimplementować jako wywołania asynchroniczne lub implementacje lub nie, w stosownych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="220d3-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="220d3-181">Ogólnie rzecz biorąc, gdy umowa jest wymiana komunikatów jednokierunkowych, implementacje mogą być w dużej mierze asynchroniczne, ponieważ po wysłaniu wiadomości aplikacja nie czeka na odpowiedź i może kontynuować wykonywanie innych prac.</span><span class="sxs-lookup"><span data-stu-id="220d3-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="220d3-182">Asynchronii klienci i kontrakty wiadomości oparte na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="220d3-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="220d3-183">Wytyczne projektowe dla stanu modelu asynchroniowego opartego na zdarzeniach, że jeśli `Result` zwracana jest więcej niż jedna <xref:System.EventArgs> wartość, jedna wartość jest zwracana jako właściwość, a pozostałe są zwracane jako właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="220d3-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="220d3-184">Jednym z wyników jest to, że jeśli klient importuje metadane przy użyciu opcji polecenia asynchronicznego opartego na zdarzeniach, a operacja zwraca więcej niż jedną wartość, domyślny <xref:System.EventArgs> obiekt zwraca jedną wartość jako `Result` właściwość, a pozostała część to właściwości <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="220d3-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="220d3-185">Jeśli chcesz otrzymać obiekt wiadomości `Result` jako właściwość i mieć zwrócone wartości jako właściwości tego obiektu, użyj opcji polecenia **/messageContract.**</span><span class="sxs-lookup"><span data-stu-id="220d3-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="220d3-186">Spowoduje to wygenerowanie podpisu, który `Result` zwraca <xref:System.EventArgs> komunikat odpowiedzi jako właściwość na obiekcie.</span><span class="sxs-lookup"><span data-stu-id="220d3-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="220d3-187">Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="220d3-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220d3-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="220d3-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
