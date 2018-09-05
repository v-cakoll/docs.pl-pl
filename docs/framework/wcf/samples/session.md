---
title: Sesja
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: ce91adbb5156eef09221a76773e5a9551f0e8440
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517895"
---
# <a name="session"></a><span data-ttu-id="e77ce-102">Sesja</span><span class="sxs-lookup"><span data-stu-id="e77ce-102">Session</span></span>
<span data-ttu-id="e77ce-103">Przykładowe sesji demonstruje sposób implementacji kontraktu wymagającego sesji.</span><span class="sxs-lookup"><span data-stu-id="e77ce-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="e77ce-104">Sesja tworzy kontekst do wykonywania wielu operacji.</span><span class="sxs-lookup"><span data-stu-id="e77ce-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="e77ce-105">Umożliwia usłudze kojarzenie stanu z danej sesji, takie, że kolejne operacje można użyć stanu poprzednią operację.</span><span class="sxs-lookup"><span data-stu-id="e77ce-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="e77ce-106">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="e77ce-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="e77ce-107">`ICalculator` Kontraktu została zmodyfikowana, aby zezwolić na zestaw operacji arytmetycznych do wykonania przy jednoczesnym zachowaniu wynik uruchomionych.</span><span class="sxs-lookup"><span data-stu-id="e77ce-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="e77ce-108">Ta funkcja jest zdefiniowana przez `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e77ce-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="e77ce-109">Jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń Usługa przechowuje informacje o stanie dla klienta.</span><span class="sxs-lookup"><span data-stu-id="e77ce-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="e77ce-110">Klient może pobrać bieżący wynik, wywołując `Result()` i wyczyść wynik, który ma wartość zero, wywołując `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="e77ce-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="e77ce-111">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="e77ce-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e77ce-112">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e77ce-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e77ce-113">Ustawienie <xref:System.ServiceModel.SessionMode> kontraktu na `Required` gwarantuje, że Umowa ujawniane za pośrednictwem określonego powiązania powiązanie obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="e77ce-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="e77ce-114">Jeśli wiązanie nie obsługuje sesji jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e77ce-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="e77ce-115">`ICalculatorSession` Interfejsu jest zdefiniowana taki sposób, że co najmniej jednej operacji może być wywoływana, co modyfikuje uruchomionej wynik, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e77ce-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="e77ce-116">Używa usługi <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.PerSession> powiązać każdej przychodzących sesji kontekstu wystąpienie danej usługi.</span><span class="sxs-lookup"><span data-stu-id="e77ce-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="e77ce-117">Dzięki temu usługa do obsługi uruchomionych wyników dla każdej sesji w zmiennej składowej lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e77ce-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="e77ce-118">Po uruchomieniu przykładu, klient wysyła wiele żądań do serwera i żąda wynik, który następnie zostanie wyświetlony w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e77ce-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="e77ce-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e77ce-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e77ce-120">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="e77ce-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e77ce-121">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e77ce-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e77ce-122">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e77ce-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e77ce-123">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e77ce-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e77ce-124">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e77ce-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e77ce-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e77ce-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e77ce-126">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e77ce-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e77ce-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e77ce-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="e77ce-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e77ce-128">See Also</span></span>
