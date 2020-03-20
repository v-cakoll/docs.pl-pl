---
title: Sesja
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183361"
---
# <a name="session"></a><span data-ttu-id="7212d-102">Sesja</span><span class="sxs-lookup"><span data-stu-id="7212d-102">Session</span></span>
<span data-ttu-id="7212d-103">Przykład sesji pokazuje, jak zaimplementować kontrakt, który wymaga sesji.</span><span class="sxs-lookup"><span data-stu-id="7212d-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="7212d-104">Sesja zawiera kontekst do wykonywania wielu operacji.</span><span class="sxs-lookup"><span data-stu-id="7212d-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="7212d-105">Dzięki temu usługa do skojarzenia stanu z danej sesji, tak, że kolejne operacje można użyć stanu poprzedniej operacji.</span><span class="sxs-lookup"><span data-stu-id="7212d-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="7212d-106">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="7212d-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="7212d-107">Kontrakt `ICalculator` został zmodyfikowany, aby umożliwić zestaw operacji arytmetycznych do wykonania, przy zachowaniu wyniku bieżącego.</span><span class="sxs-lookup"><span data-stu-id="7212d-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="7212d-108">Ta funkcja jest zdefiniowana `ICalculatorSession` przez kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7212d-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="7212d-109">Usługa utrzymuje stan dla klienta, jak wiele operacji usługi są wywoływane do wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7212d-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="7212d-110">Klient może pobrać bieżący wynik, wywołując `Result()` i wyczyścić `Clear()`wynik do zera, wywołując .</span><span class="sxs-lookup"><span data-stu-id="7212d-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="7212d-111">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="7212d-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7212d-112">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7212d-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7212d-113"><xref:System.ServiceModel.SessionMode> Ustawienie umowy, `Required` aby upewnić się, że gdy umowa jest narażona na określone powiązanie, powiązanie obsługuje sesje.</span><span class="sxs-lookup"><span data-stu-id="7212d-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="7212d-114">Jeśli powiązanie nie obsługuje sesji wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7212d-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="7212d-115">Interfejs `ICalculatorSession` jest zdefiniowany w taki sposób, że można wywołać jedną lub więcej operacji, co modyfikuje wynik uruchomiony, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7212d-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="7212d-116">Usługa używa a <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> do powiązania kontekstu wystąpienia danej usługi do każdej sesji przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="7212d-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="7212d-117">Dzięki temu usługa do utrzymania bieżącego wyniku dla każdej sesji w zmiennej lokalnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7212d-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="7212d-118">Po uruchomieniu próbki klient wysunie kilka żądań do serwera i żąda wyniku, który następnie wyświetla w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7212d-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="7212d-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7212d-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7212d-120">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="7212d-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7212d-121">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7212d-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7212d-122">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7212d-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7212d-123">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7212d-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7212d-124">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7212d-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7212d-125">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="7212d-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7212d-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="7212d-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7212d-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7212d-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
