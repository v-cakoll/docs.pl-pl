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
ms.openlocfilehash: c2948cf76f7763eae51689973346965bc6c720a8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171299"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="000b7-102">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="000b7-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="000b7-103">W tym temacie omówiono wdrażanie i wywoływanie operacji usługi asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="000b7-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="000b7-104">Wiele aplikacji asynchroniczne wywoływanie metod, ponieważ umożliwia aplikacji do kontynuowania wykonywania użytecznej pracy podczas wykonywania wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="000b7-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="000b7-105">Usług Windows Communication Foundation (WCF) i klientów, które mogą uczestniczyć w operacji asynchronicznej wywołań na dwóch różnych poziomach aplikacji, zapewniający jeszcze większą elastyczność w celu zmaksymalizowania wydajności zrównoważone interakcję aplikacji WCF .</span><span class="sxs-lookup"><span data-stu-id="000b7-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="000b7-106">Rodzaje operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="000b7-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="000b7-107">Wszystkie usługi kontraktów w programie WCF, bez względu na to typy parametrów i wartości zwracane, użyj atrybutów usługi WCF do określenia wymiany komunikatów określonej między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="000b7-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="000b7-108">Usługi WCF automatycznie kieruje komunikaty przychodzące i wychodzące operacji odpowiednie usługi lub uruchamianie kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="000b7-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="000b7-109">Klient ma tylko kontraktu usługi, który określa wymiany komunikatów dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="000b7-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="000b7-110">Klienci mogą zaoferować łączność dewelopera model programowania, które postanowili, tak długo, jak zostanie wykryty bazowego wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="000b7-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="000b7-111">Dlatego, można usług implementowania operacji w jakikolwiek sposób, tak długo, jak zostanie wykryty wzorzec określony komunikat.</span><span class="sxs-lookup"><span data-stu-id="000b7-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="000b7-112">Niezależność od implementacji usługi lub klienta kontraktu usługi umożliwia następujące rodzaje operacji asynchronicznych w aplikacjach usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="000b7-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
-   <span data-ttu-id="000b7-113">Klientów można wywołać operacji żądania/odpowiedzi asynchronicznie za pomocą wymiany synchronicznego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="000b7-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="000b7-114">Usługi można zaimplementować operację żądania/odpowiedzi asynchronicznie przy użyciu synchronicznej wiadomości programu exchange.</span><span class="sxs-lookup"><span data-stu-id="000b7-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="000b7-115">Wymianę komunikatów może być jednokierunkowych, niezależnie od implementacji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="000b7-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="000b7-116">Scenariusze asynchroniczne z sugerowanych</span><span class="sxs-lookup"><span data-stu-id="000b7-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="000b7-117">Asynchroniczne metody należy użyć w implementacji operacji usługi, jeśli operacja implementacji usługi sprawia, że wywołania blokowania, takich jak praca operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="000b7-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="000b7-118">Podczas pracy w celu wykonania operacji asynchronicznej, spróbuj wywołać operacji asynchronicznych i metody, aby rozszerzyć ścieżki wywołania asynchronicznego, o ile to możliwe.</span><span class="sxs-lookup"><span data-stu-id="000b7-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="000b7-119">Na przykład wywołać `BeginOperationTwo()` z poziomu `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="000b7-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="000b7-120">Użyj podejścia asynchroniczne w kliencie lub aplikacja wywołująca w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="000b7-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="000b7-121">Jeśli są wywoływanie operacji z aplikacji średniego poziomu.</span><span class="sxs-lookup"><span data-stu-id="000b7-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="000b7-122">(Aby uzyskać więcej informacji na temat takich scenariuszy, zobacz [aplikacje klienckie warstwy środkowej](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="000b7-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="000b7-123">Jeśli są wywoływanie operacji w obrębie strony ASP.NET, należy użyć strony asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="000b7-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="000b7-124">Jeśli są wywoływanie operacji z dowolnej aplikacji, która ma jeden wątków, takich jak Windows Forms lub Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="000b7-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="000b7-125">Korzystając z opartego na zdarzeniach asynchronicznych wywoływania modelu, zdarzenie wynik jest wywoływane w wątku interfejsu użytkownika, dodając czas odpowiedzi do aplikacji bez konieczności obsługi wielu wątków, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="000b7-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="000b7-126">Ogólnie rzecz biorąc należy dokonać wyboru między wywołania synchroniczne i asynchroniczne, jeśli wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="000b7-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="000b7-127">Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="000b7-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="000b7-128">Operacje asynchroniczne można zaimplementować przy użyciu jednej z trzech poniższych metod:</span><span class="sxs-lookup"><span data-stu-id="000b7-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="000b7-129">Wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="000b7-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="000b7-130">Asynchroniczny wzorzec oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="000b7-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="000b7-131">Wzorzec asynchroniczny IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="000b7-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="000b7-132">Wzorzec asynchroniczny oparty na zadanie</span><span class="sxs-lookup"><span data-stu-id="000b7-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="000b7-133">Wzorca asynchronicznego opartego na zadaniach jest preferowany sposób implementowania asynchronicznych operacji, ponieważ jest najłatwiejszym i najbardziej bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="000b7-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="000b7-134">Aby użyć tej metody po prostu implementuje operację usługi i określ typu zwracanego zadania\<T >, gdzie T jest typem zwracanym przez operacji logicznej.</span><span class="sxs-lookup"><span data-stu-id="000b7-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="000b7-135">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="000b7-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="000b7-136">Operacja SampleMethodTaskAsync zwraca zadanie\<ciągu > ponieważ operacja logiczna zwraca wartość typu ciąg.</span><span class="sxs-lookup"><span data-stu-id="000b7-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="000b7-137">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [wzorca asynchronicznego The Task-Based](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="000b7-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="000b7-138">Korzystając z wzorca asynchronicznego opartego na zadaniach, T:System.AggregateException mogą być generowane, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="000b7-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="000b7-139">Ten wyjątek może wystąpić na kliencie lub usług</span><span class="sxs-lookup"><span data-stu-id="000b7-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="000b7-140">Wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="000b7-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="000b7-141">Obsługującego wzorzec asynchroniczny oparty na zdarzeniach usługi ma co najmniej jednej operacji o nazwie MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="000b7-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="000b7-142">Te metody mogą dublować synchroniczne wersjach, które do tej samej operacji w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="000b7-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="000b7-143">Klasa może mieć również zdarzenia MethodNameCompleted i może mieć MethodNameAsyncCancel (lub po prostu CancelAsync) metody.</span><span class="sxs-lookup"><span data-stu-id="000b7-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="000b7-144">Klient dążące do wywołania operacji będą definiować program obsługi zdarzeń ma być wywoływana po zakończeniu tej operacji</span><span class="sxs-lookup"><span data-stu-id="000b7-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="000b7-145">Poniższy fragment kodu ilustruje sposób deklarowania operacji asynchronicznych z użyciem wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="000b7-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="000b7-146">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zdarzeniach zobacz [wzorca asynchronicznego The Event-Based](https://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="000b7-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="000b7-147">Wzorzec asynchroniczny IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="000b7-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="000b7-148">Operacja usługi może być implementowany w sposób asynchroniczny za pomocą [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronicznego programowania wzorca i oznaczanie `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwością `true`.</span><span class="sxs-lookup"><span data-stu-id="000b7-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="000b7-149">W takim przypadku operacja asynchroniczna jest widoczna w metadanych, w tym samym formularzu jako operacja synchroniczna: jest ona uwidoczniona jako jedną operację przy użyciu komunikatu żądania i komunikat odpowiedzi skorelowane.</span><span class="sxs-lookup"><span data-stu-id="000b7-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="000b7-150">Modele programowania klient następnie dokonać wyboru.</span><span class="sxs-lookup"><span data-stu-id="000b7-150">Client programming models then have a choice.</span></span> <span data-ttu-id="000b7-151">Mogą one reprezentować tego wzorca jako operacji synchronicznych lub asynchronicznych, co tak długo, jak podczas wywoływania usługi wymianę komunikatów żądań i odpowiedzi ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="000b7-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="000b7-152">Ogólnie rzecz biorąc za pomocą asynchronicznego charakter tych systemów, możesz nie powinna przyjmować zależności na wątki.</span><span class="sxs-lookup"><span data-stu-id="000b7-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="000b7-153">Najbardziej niezawodnym sposobem przekazywanie danych do różnych etapów przetwarzania wysyłania operacji jest korzystanie z rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="000b7-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="000b7-154">Aby uzyskać przykład, zobacz [porady: Wdrażanie asynchronicznej operacji usługi](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="000b7-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="000b7-155">Aby zdefiniować operacji kontraktu `X` asynchronicznie wykonywane niezależnie od tego, jak jest to aplikacja kliencka:</span><span class="sxs-lookup"><span data-stu-id="000b7-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="000b7-156">Zdefiniowanie dwóch metod przy użyciu wzorca `BeginOperation` i `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="000b7-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="000b7-157">`BeginOperation` Metoda zawiera `in` i `ref` parametrów operacji i zwraca <xref:System.IAsyncResult> typu.</span><span class="sxs-lookup"><span data-stu-id="000b7-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="000b7-158">`EndOperation` Metoda zawiera <xref:System.IAsyncResult> parametru, jak również `out` i `ref` parametrów i zwraca operacje typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="000b7-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="000b7-159">Na przykład zobacz następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="000b7-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="000b7-160">Aby utworzyć operację asynchroniczną, będzie dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="000b7-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
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
>  <span data-ttu-id="000b7-161"><xref:System.ServiceModel.OperationContractAttribute> Atrybut jest stosowany tylko do `BeginDoWork` metody.</span><span class="sxs-lookup"><span data-stu-id="000b7-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="000b7-162">Kontrakt wynikowy ma jedną operację WSDL o nazwie `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="000b7-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="000b7-163">Wywołania asynchroniczne po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="000b7-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="000b7-164">Aplikacja klienta WCF można użyć dowolnego z trzy modele wywołania asynchronicznego opisanych powyżej</span><span class="sxs-lookup"><span data-stu-id="000b7-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="000b7-165">Korzystając z modelu opartego na zadaniach, wystarczy wywołać operację, używając słowa kluczowego await, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="000b7-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="000b7-166">Za pomocą wzorca asynchronicznego opartego na zdarzeniach wymaga tylko dodanie, którego program obsługi zdarzeń, aby otrzymać powiadomienie w odpowiedzi — i wynikowy zdarzenie jest wywoływane w wątku interfejsu użytkownika automatycznie.</span><span class="sxs-lookup"><span data-stu-id="000b7-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="000b7-167">Aby użyć tej metody, należy określić zarówno **/async** i **/tcv:Version35** opcji za pomocą polecenia [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w następujących przykład.</span><span class="sxs-lookup"><span data-stu-id="000b7-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="000b7-168">Po zakończeniu tej operacji Svcutil.exe wygeneruje klasy klienta WCF, za pomocą infrastruktury zdarzeń, który umożliwia aplikacji wywołującej zaimplementować i przypisać program obsługi zdarzeń, odebranie odpowiedzi i podejmij odpowiednie działanie.</span><span class="sxs-lookup"><span data-stu-id="000b7-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="000b7-169">Aby uzyskać kompletny przykład, zobacz [porady: wywoływanie operacji usługi asynchronicznie](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="000b7-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="000b7-170">Oparte na zdarzeniach modelu asynchronicznego, jednak jest dostępna tylko w [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="000b7-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="000b7-171">Ponadto nie jest obsługiwana nawet w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] po utworzeniu kanału klienta programu WCF za pomocą <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="000b7-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="000b7-172">Za pomocą obiektów kanału klienta WCF, należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do wywołania operacji asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="000b7-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="000b7-173">Aby użyć tej metody, należy określić **/async** opcja za pomocą polecenia [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="000b7-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="000b7-174">Spowoduje to wygenerowanie kontraktu usługi, w którym każda operacja ma formę `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwością `true` i odpowiadający mu `<End>` metody.</span><span class="sxs-lookup"><span data-stu-id="000b7-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="000b7-175">Aby uzyskać kompletny przykład za pomocą <xref:System.ServiceModel.ChannelFactory%601>, zobacz [jak: wywołanie operacji asynchronicznie za pomocą fabryki kanałów](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="000b7-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="000b7-176">W obu przypadkach aplikacje mogą wywołać operację asynchronicznie, nawet wtedy, gdy usługa jest wdrażana synchronicznie, w taki sam sposób, który aplikacja może użyć tego samego wzorca do wywołania asynchronicznego lokalnego metoda synchroniczna.</span><span class="sxs-lookup"><span data-stu-id="000b7-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="000b7-177">Jak zaimplementowano operacji nie jest istotny dla klienta; Po odebraniu komunikatu odpowiedzi jego zawartość jest wysyłane do klienta asynchronicznego <`End`> Metoda i klient pobiera informacje.</span><span class="sxs-lookup"><span data-stu-id="000b7-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="000b7-178">Komunikat jednokierunkowy Exchange wzorców</span><span class="sxs-lookup"><span data-stu-id="000b7-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="000b7-179">Można też utworzyć wymiany komunikatów asynchronicznych, w jakie operacje jednokierunkowe (operacji, dla którego <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> jest `true` nie skorelowany odpowiedź) mogą być wysyłane przez klienta lub usługę niezależnie w dowolnym kierunku Strona.</span><span class="sxs-lookup"><span data-stu-id="000b7-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="000b7-180">(To za pomocą wymiany komunikatów dwukierunkowego jednokierunkowe komunikaty.) W tym przypadku kontrakt usługi Określa komunikat jednokierunkowy programu exchange, który po obu stronach można zaimplementować jako wywołania asynchronicznego lub implementacji lub nie, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="000b7-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="000b7-181">Ogólnie rzecz biorąc gdy kontrakt jest wymiany jednokierunkowe komunikaty, implementacje stopniu można asynchronicznego ponieważ po wysłaniu komunikatu aplikacji nie czeka na odpowiedź i można kontynuować inne prace.</span><span class="sxs-lookup"><span data-stu-id="000b7-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="000b7-182">Oparte na zdarzeniach asynchronicznych klientów i kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="000b7-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="000b7-183">Dotyczących projektowania opartego na zdarzeniach modelu asynchronicznego stanu, że jeśli zwracana jest więcej niż jedną wartość, jedną wartość jest zwracana jako `Result` właściwości i inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="000b7-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="000b7-184">Jeden wynik tego jest to, że jeśli klient importuje metadane przy użyciu opcji oparte na zdarzeniach asynchronicznych polecenia, a operacja zwraca więcej niż jedną wartość, wartość domyślna <xref:System.EventArgs> zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="000b7-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="000b7-185">Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mają zwracanych wartości, jak używać właściwości dla tego obiektu **/messageContract** opcja polecenia.</span><span class="sxs-lookup"><span data-stu-id="000b7-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="000b7-186">Spowoduje to wygenerowanie sygnaturę, która zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="000b7-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="000b7-187">Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="000b7-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000b7-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="000b7-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
