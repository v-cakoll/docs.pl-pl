---
title: Operacje synchroniczne i asynchroniczne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fce4129924b4f0ce4542f2d274d2cc4031928c9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="5a4f9-102">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="5a4f9-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="5a4f9-103">W tym temacie omówiono Implementowanie i wywoływanie operacji usługi asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="5a4f9-104">Wiele aplikacji asynchroniczne wywoływanie metody, ponieważ umożliwia to aplikacji kontynuować pracy przydatne podczas wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="5a4f9-105">usługi i klienci mogą uczestniczyć w wywołania operacji asynchronicznej na dwóch różnych poziomach aplikacji, które zawierają [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji nawet większą elastyczność i możliwość zmaksymalizować przepustowość zrównoważone interakcji.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-105"> services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="5a4f9-106">Typy operacji asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="5a4f9-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="5a4f9-107">Wszystkie usługi umów [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bez względu na typy parametrów i wartości zwracane, użyj [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] atrybutów, aby określić konkretnego wymiany komunikatów między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-107">All service contracts in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], no matter the parameters types and return values, use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] attributes to specify a particular message exchange pattern between client and service.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="5a4f9-108">automatycznie kieruje komunikaty przychodzące i wychodzące z operacją odpowiednią usługę lub wykonywanie kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-108"> automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="5a4f9-109">Klient ma tylko kontraktu usługi, która określa wymiany komunikatów dla określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="5a4f9-110">Klienci zaoferować dewelopera dowolnego modelu programowania, które decydują, tak długo, jak zaobserwowano podstawowej wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="5a4f9-111">Tak zbyt, usługi zaimplementować operacji w jakikolwiek sposób tak długo, jak zaobserwowano wzorzec określonego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="5a4f9-112">Niezależność od usługi umowy z dowolnej usługi lub klienta implementacja zapewnia następujące rodzaje operacji asynchronicznych w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="5a4f9-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="5a4f9-113">Klienci mogą wywoływać operacje żądania/odpowiedzi asynchronicznie za pomocą exchange komunikatu synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="5a4f9-114">Usługi można zaimplementować operacji żądania/odpowiedzi, asynchronicznie za pomocą exchange komunikatu synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="5a4f9-115">Wymiany komunikatów może być jednokierunkowe, niezależnie od implementacji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="5a4f9-116">Sugerowana scenariusze asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="5a4f9-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="5a4f9-117">Asynchroniczne metody należy użyć w implementacji operacji usługi, jeśli operacja implementacji usługi nawiązuje połączenie blokujące, takie jak podczas pracy we/wy.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="5a4f9-118">Podczas pracy w celu wykonania operacji asynchronicznej, spróbuj wywołanie operacji asynchronicznych i metody umożliwiające rozszerzenie ścieżki wywołania asynchronicznego, o ile to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="5a4f9-119">Na przykład wywołać `BeginOperationTwo()` z poziomu `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="5a4f9-120">Przy użyciu asynchronicznej metody na kliencie lub aplikacja wywołująca w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="5a4f9-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="5a4f9-121">Jeśli są wywoływanie operacji aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="5a4f9-122">([!INCLUDE[crabout](../../../includes/crabout-md.md)] takich scenariuszy, zobacz [aplikacje klienckie warstwy środkowej](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="5a4f9-122">([!INCLUDE[crabout](../../../includes/crabout-md.md)] such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="5a4f9-123">Jeśli są wywoływania operacji strony ASP.NET, użyj stron asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="5a4f9-124">Jeśli są wywoływania operacji z dowolnej aplikacji, która jest pojedynczym wątków, takie jak formularze systemu Windows lub [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a4f9-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="5a4f9-125">Korzystając z oparty na zdarzeniach asynchroniczne wywołanie modelu, zdarzenie wynik jest wywoływane w wątku interfejsu użytkownika, dodawanie czas odpowiedzi aplikacji bez konieczności się obsługiwać wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="5a4f9-126">Ogólnie rzecz biorąc Jeśli masz wybór między wywołania synchroniczne i asynchroniczne, wybierz wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="5a4f9-127">Wdrażanie asynchronicznej operacji usługi</span><span class="sxs-lookup"><span data-stu-id="5a4f9-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="5a4f9-128">Operacje asynchroniczne może być zaimplementowany przez przy użyciu jednej z trzech następujących metod:</span><span class="sxs-lookup"><span data-stu-id="5a4f9-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="5a4f9-129">Asynchroniczny wzorzec oparty na zadaniach</span><span class="sxs-lookup"><span data-stu-id="5a4f9-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="5a4f9-130">Asynchroniczny wzorzec oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="5a4f9-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="5a4f9-131">Asynchroniczny wzorzec IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="5a4f9-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="5a4f9-132">Wzorzec asynchroniczny oparty na zadaniach</span><span class="sxs-lookup"><span data-stu-id="5a4f9-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="5a4f9-133">Asynchroniczny wzorzec oparty na zadaniach jest preferowany sposób implementowania operacji asynchronicznych, ponieważ jest najprostsza i większość bezpośrednio do przodu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="5a4f9-134">Aby użyć tej metody po prostu implementuje operację usługi i określić zwracanego typu zadania\<T >, gdzie T jest typem zwracanym przez operacji logicznej.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="5a4f9-135">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5a4f9-135">For example:</span></span>  
  
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
  
 <span data-ttu-id="5a4f9-136">Operacja SampleMethodTaskAsync zwraca zadanie\<ciągu >, ponieważ operacja logiczna zwraca wartość typu ciąg.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="5a4f9-137">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [wzorca asynchronicznego The Task-Based](http://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="5a4f9-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5a4f9-138">Podczas korzystania z wzorca asynchronicznego opartego na zadaniach, T:System.AggregateException może zostać zgłoszony, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="5a4f9-139">Ten wyjątek może wystąpić na kliencie lub usług</span><span class="sxs-lookup"><span data-stu-id="5a4f9-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="5a4f9-140">Wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="5a4f9-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="5a4f9-141">Obsługującego wzorzec asynchroniczny oparty na zdarzeniach usługi ma co najmniej jedną operację o nazwie MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="5a4f9-142">Te metody mogą duplikatów synchroniczne wersje, które do tej samej operacji w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="5a4f9-143">Klasa może być również zdarzeń MethodNameCompleted i może mieć MethodNameAsyncCancel (lub po prostu CancelAsync) metody.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="5a4f9-144">Klient chcą wywołaj operację określi program obsługi zdarzeń ma być wywoływana po zakończeniu operacji</span><span class="sxs-lookup"><span data-stu-id="5a4f9-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="5a4f9-145">Poniższy fragment kodu ilustruje sposób zadeklarować operacji asynchronicznych za pomocą wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
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
  
 <span data-ttu-id="5a4f9-146">Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zdarzeniach, zobacz [wzorca asynchronicznego The Event-Based](http://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="5a4f9-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="5a4f9-147">Wzorzec projektowy IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="5a4f9-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="5a4f9-148">Operacja usługi może być wdrożonych w sposób asynchroniczny przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programowania wzorca asynchronicznego i oznaczenie `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> ustawioną właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="5a4f9-149">W takim przypadku operacja asynchroniczna jest widoczna w metadanych, w tym samym formularzu jako operacja synchroniczna: jest uwidaczniany jako jedna operacja z komunikatu żądania i komunikat odpowiedzi skorelowane.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="5a4f9-150">Modele programowania klient następnie mają wybór.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-150">Client programming models then have a choice.</span></span> <span data-ttu-id="5a4f9-151">Reprezentują tego wzorca jako operacja synchroniczna lub asynchroniczne jedna tak długo, jak długo po wywołaniu usługi wymiany komunikatów żądań i odpowiedzi ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="5a4f9-152">Ogólnie rzecz biorąc z asynchronicznego charakter systemów, możesz nie powinna przyjmować zależności na wątki.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="5a4f9-153">Najbardziej niezawodnym sposobem przekazywanie danych do różnych etapów przetwarzania wysyłania operacji jest używanie rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="5a4f9-154">Na przykład zobacz [porady: Implementowanie asynchronicznej operacji usługi](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="5a4f9-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="5a4f9-155">Aby zdefiniować operacja kontraktu `X` asynchronicznie wykonywane niezależnie od tego, jak jest to aplikacja klienta:</span><span class="sxs-lookup"><span data-stu-id="5a4f9-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="5a4f9-156">Zdefiniuj dwie metody przy użyciu wzorca `BeginOperation` i `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="5a4f9-157">`BeginOperation` Metoda zawiera `in` i `ref` parametrów operacji i zwraca <xref:System.IAsyncResult> typu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="5a4f9-158">`EndOperation` Metoda zawiera <xref:System.IAsyncResult> parametru, jak również `out` i `ref` parametrów i zwraca operacje typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="5a4f9-159">Na przykład zobacz następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="5a4f9-160">Aby utworzyć operację asynchroniczną, będzie dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="5a4f9-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <span data-ttu-id="5a4f9-161"><xref:System.ServiceModel.OperationContractAttribute> Atrybut jest stosowany tylko do `BeginDoWork` metody.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="5a4f9-162">Wynikowa kontraktu ma jedną operację WSDL o nazwie `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="5a4f9-163">Asynchroniczne wywołania po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="5a4f9-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="5a4f9-164">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta aplikacji można użyć dowolnego z trzy modele wywołanie asynchroniczne opisanych powyżej</span><span class="sxs-lookup"><span data-stu-id="5a4f9-164">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="5a4f9-165">Gdy używany jest model oparty na zadaniach, po prostu wywołaj operację przy użyciu — słowo kluczowe await, jak pokazano w poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="5a4f9-166">Za pomocą wzorca asynchronicznego opartego na zdarzeniach wymaga tylko dodanie przez program obsługi zdarzeń, aby otrzymać powiadomienie o odpowiedź--i wynikowy zdarzenie jest wywoływane w wątku interfejsu użytkownika automatycznie.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="5a4f9-167">Aby użyć tej metody, należy określić zarówno **/async** i **/tcv:Version35** polecenie Opcje z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykład.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="5a4f9-168">Po zakończeniu Svcutil.exe generuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klasy klienta przy użyciu infrastruktury zdarzeń, który umożliwia wywołanie aplikacji do wdrożenia i przypisać program obsługi zdarzeń do odbierania odpowiedzi i podejmij odpowiednie działanie.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-168">When this is done, Svcutil.exe generates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="5a4f9-169">Pełny przykład, zobacz [porady: wywołania operacji usługi asynchronicznie](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="5a4f9-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="5a4f9-170">Oparty na zdarzeniach modelu asynchroniczne, jednak jest dostępna tylko w [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a4f9-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="5a4f9-171">Ponadto nie jest obsługiwane nawet w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] podczas [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanału klienta jest tworzona przy użyciu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a4f9-172">Z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiekty kanału klienta, należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do asynchronicznego wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-172">With [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="5a4f9-173">Aby użyć tej metody, podaj **/async** polecenia opcji [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="5a4f9-174">Spowoduje to wygenerowanie kontraktu usługi, w której każda operacja ma formę `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> ustawioną właściwość `true` i odpowiadające mu `<End>` — metoda.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="5a4f9-175">Aby uzyskać pełny przykład za pomocą <xref:System.ServiceModel.ChannelFactory%601>, zobacz [jak: wywołanie operacji asynchronicznie przy użyciu fabryki kanałów](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="5a4f9-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="5a4f9-176">W obu przypadkach aplikacji można wywołać operacji asynchronicznie, nawet wtedy, gdy usługa jest wdrażana synchronicznie, w taki sam sposób, że aplikacja może użyć tego samego wzorca do asynchronicznego wywołania lokalnego metoda synchroniczna.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="5a4f9-177">Implementowania operacji nie jest znacząca klientowi; Po odebraniu wiadomości odpowiedzi, jego zawartość jest wysyłane do klienta asynchroniczne <`End`> Metoda i klient pobiera informacje.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="5a4f9-178">Komunikat jednokierunkowy wzorce programu Exchange</span><span class="sxs-lookup"><span data-stu-id="5a4f9-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="5a4f9-179">Asynchroniczne wymiany komunikatów można też utworzyć, w których operacji jednokierunkowych (operacje, dla którego <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> jest `true` mieć żadnej odpowiedzi skorelowane) mogą być wysyłane przez klienta lub usługę, niezależnie od drugiego w żadnym kierunku Strona.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="5a4f9-180">(Używa dupleksu wymiany komunikatów o jednokierunkowe komunikaty.) W takim przypadku kontrakt usługi Określa komunikat jednokierunkowy programu exchange, które można wdrożyć obok jako wywołania asynchroniczne lub implementacje lub nie, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="5a4f9-181">Ogólnie rzecz biorąc gdy kontrakt jest wymiany jednokierunkowe komunikaty, implementacje przede wszystkim można asynchronicznego, ponieważ po wysłaniu komunikatu aplikacji bez oczekiwania na odpowiedź i można kontynuować wykonywania innych zadań.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="5a4f9-182">Oparty na zdarzeniach asynchroniczne klientów i kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="5a4f9-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="5a4f9-183">Wskazówek dotyczących modelu asynchroniczny oparty na zdarzeniach stanu, że jeśli zostanie zwrócony więcej niż jedną wartość, jedna wartość jest zwracana jako `Result` właściwości, a inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="5a4f9-184">Jeden wynik tego jest to, że jeśli klient importuje metadanych za pomocą opcji polecenia asynchroniczny oparty na zdarzeniach i operacji zwraca więcej niż jedną wartość, domyślna <xref:System.EventArgs> obiektu zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="5a4f9-185">Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mieć zwracanych wartości jako właściwości tego obiektu, użyj **/messageContract** — opcja polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="5a4f9-186">Spowoduje to wygenerowanie podpisie, który zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="5a4f9-187">Wszystkie wewnętrzny zwracanych wartości są następnie właściwości obiektu komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5a4f9-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4f9-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a4f9-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
