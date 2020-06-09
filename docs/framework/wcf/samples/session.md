---
title: Sesja
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 283c8b9641dcce8b0207d3be0024b57369d125ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591455"
---
# <a name="session"></a><span data-ttu-id="0c1c8-102">Sesja</span><span class="sxs-lookup"><span data-stu-id="0c1c8-102">Session</span></span>
<span data-ttu-id="0c1c8-103">Przykład sesji demonstruje sposób implementacji kontraktu wymagającego sesji.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="0c1c8-104">Sesja zawiera kontekst do wykonywania wielu operacji.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="0c1c8-105">Umożliwia to usłudze kojarzenie stanu z daną sesją, tak aby kolejne operacje mogły korzystać z stanu poprzedniej operacji.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="0c1c8-106">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md), który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-106">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="0c1c8-107">`ICalculator`Kontrakt został zmodyfikowany w taki sposób, aby zezwalał na wykonywanie zestawu operacji arytmetycznych przy zachowaniu uruchomionego wyniku.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="0c1c8-108">Ta funkcja jest definiowana przez `ICalculatorSession` umowę.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="0c1c8-109">Usługa zachowuje stan klienta w miarę wywoływania wielu operacji usługi, aby wykonać obliczenia.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="0c1c8-110">Klient może pobrać bieżący wynik, wywołując `Result()` i czyszcząc wynik do zera przez wywołanie metody `Clear()` .</span><span class="sxs-lookup"><span data-stu-id="0c1c8-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="0c1c8-111">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="0c1c8-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c1c8-112">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0c1c8-113">Ustawienie <xref:System.ServiceModel.SessionMode> kontraktu `Required` zapewnia, że gdy kontrakt zostanie ujawniony nad określonym powiązaniem, powiązanie obsługuje sesje.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="0c1c8-114">Jeśli powiązanie nie obsługuje sesji, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="0c1c8-115">`ICalculatorSession`Interfejs jest zdefiniowany w taki sposób, że można wywołać jedną lub więcej operacji, co powoduje modyfikację uruchomionego wyniku, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="0c1c8-116">Usługa używa programu w <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> celu powiązania danego kontekstu wystąpienia usługi z każdą sesją przychodzącą.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="0c1c8-117">Dzięki temu usługa może zachować wynik działania dla każdej sesji w lokalnej zmiennej członkowskiej.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="0c1c8-118">Po uruchomieniu przykładu klient wysyła kilka żądań do serwera i żąda wyniku, który następnie jest wyświetlany w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="0c1c8-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0c1c8-120">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="0c1c8-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0c1c8-121">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c1c8-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0c1c8-122">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c1c8-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0c1c8-123">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c1c8-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0c1c8-124">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0c1c8-125">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="0c1c8-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0c1c8-126">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0c1c8-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0c1c8-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
