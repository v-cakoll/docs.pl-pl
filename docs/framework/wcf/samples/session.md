---
title: Sesja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01c1bc2d202080349db32452adfe549d7a6dd3cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="session"></a><span data-ttu-id="c4fd8-102">Sesja</span><span class="sxs-lookup"><span data-stu-id="c4fd8-102">Session</span></span>
<span data-ttu-id="c4fd8-103">Przykładowe sesji demonstracja Implementowanie kontraktu wymagającego sesji.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="c4fd8-104">Sesję udostępnia kontekst do wykonywania wielu operacji.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="c4fd8-105">Umożliwia usłudze skojarzenie stanu z danej sesji, w taki sposób, że kolejnych operacji można użyć stanu poprzedniej operacji.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="c4fd8-106">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="c4fd8-107">`ICalculator` Kontraktu został zmodyfikowany umożliwia zestaw operacji arytmetycznych wykonywanych przy zachowaniu uruchomionych wynik.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="c4fd8-108">Ta funkcja jest definiowana za pomocą `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="c4fd8-109">Jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń usługi przechowuje informacje o stanie dla klienta.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="c4fd8-110">Klient może pobrać bieżący wynik przez wywołanie metody `Result()` i wyczyść wynik, który ma wartość zero, wywołując `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="c4fd8-111">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c4fd8-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4fd8-112">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c4fd8-113">Ustawienie <xref:System.ServiceModel.SessionMode> kontraktu na `Required` gwarantuje, że gdy kontrakt jest ujawniany przez konkretnego powiązanie, wiązanie obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="c4fd8-114">Jeśli powiązanie nie obsługuje sesji jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="c4fd8-115">`ICalculatorSession` Interfejsu jest zdefiniowana taki sposób, że co najmniej jedną operację można wywołać, co modyfikuje uruchomionych wynik, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="c4fd8-116">Używane przez usługę <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.PerSession> powiązać kontekstu wystąpienie danej usługi do każdej sesji przychodzących.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="c4fd8-117">Dzięki temu usługi do obsługi uruchomiona wynik dla każdej sesji w zmiennej lokalnej elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="c4fd8-118">Po uruchomieniu próbki, klient wysyła kilka żądań do serwera i żąda wynik, który następnie zostanie wyświetlony w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="c4fd8-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4fd8-120">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="c4fd8-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c4fd8-121">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4fd8-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c4fd8-122">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4fd8-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c4fd8-123">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4fd8-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4fd8-124">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c4fd8-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c4fd8-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c4fd8-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4fd8-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c4fd8-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="c4fd8-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4fd8-128">See Also</span></span>
