---
title: Zgodność platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: a718b3f3bcbfd4bc2b74a14ba8f20cd8c335877f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925277"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="a0435-102">Zgodność platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a0435-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="a0435-103">Ten przykład pokazuje, jak włączyć tryb zgodności ASP.NET w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a0435-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a0435-104">Usługi działające w trybie zgodności ASP.NET uczestniczą w pełni w potoku aplikacji ASP.NET i mogą korzystać z funkcji ASP.NET, takich jak autoryzacja plików/adresów URL, <xref:System.Web.HttpContext> stan sesji i Klasa.</span><span class="sxs-lookup"><span data-stu-id="a0435-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="a0435-105"><xref:System.Web.HttpContext> Klasa umożliwia dostęp do plików cookie, sesji i innych funkcji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a0435-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="a0435-106">Ten tryb wymaga, aby powiązania korzystały z transportu HTTP i sama usługa musi być hostowana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="a0435-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="a0435-107">W tym przykładzie klient jest aplikacją konsolową (plik wykonywalny), a usługa jest hostowana w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a0435-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0435-108">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a0435-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="a0435-109">Aby można było uruchomić [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] ten przykład, wymagana jest pula aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0435-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="a0435-110">Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślną pulę aplikacji, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="a0435-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1. <span data-ttu-id="a0435-111">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="a0435-111">Open **Control Panel**.</span></span>  <span data-ttu-id="a0435-112">Otwórz aplet **Narzędzia administracyjne** w nagłówku **system i zabezpieczenia** .</span><span class="sxs-lookup"><span data-stu-id="a0435-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="a0435-113">Otwórz aplet **menedżer Internet Information Services (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="a0435-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2. <span data-ttu-id="a0435-114">Rozwiń element TreeView w okienku **połączenia** .</span><span class="sxs-lookup"><span data-stu-id="a0435-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="a0435-115">Wybierz węzeł **Pule aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="a0435-115">Select the **Application Pools** node.</span></span>  

3. <span data-ttu-id="a0435-116">Aby ustawić domyślną pulę aplikacji, która ma [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] być używana (co może spowodować problemy ze zgodnością z istniejącymi lokacjami), kliknij prawym przyciskiem myszy element listy z opcją **Domyślna** i wybierz pozycję **Ustawienia podstawowe.** .</span><span class="sxs-lookup"><span data-stu-id="a0435-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="a0435-117">Ustaw ściąganie **wersji programu .NET Framework** w **programie .NET Framework v 4.0.30128** (lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="a0435-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4. <span data-ttu-id="a0435-118">Aby utworzyć nową pulę aplikacji używaną [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] przez program (w celu zachowania zgodności z innymi aplikacjami), kliknij prawym przyciskiem myszy węzeł **Pule aplikacji** i wybierz polecenie **Dodaj pulę aplikacji.** .</span><span class="sxs-lookup"><span data-stu-id="a0435-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="a0435-119">Nadaj nazwę nowej puli aplikacji, a następnie ustaw opcję ściągania **wersji programu .NET Framework** w **programie .NET Framework v 4.0.30128** (lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="a0435-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="a0435-120">Po uruchomieniu poniższych kroków instalacji kliknij prawym przyciskiem myszy aplikację **servicemodelsamples** i wybierz pozycję **Zarządzaj aplikacją**, **Ustawienia zaawansowane...** .</span><span class="sxs-lookup"><span data-stu-id="a0435-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="a0435-121">Ustaw **pulę aplikacji** na nową pulę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0435-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0435-122">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a0435-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a0435-123">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a0435-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0435-124">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a0435-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0435-125">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a0435-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="a0435-126">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="a0435-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="a0435-127">Umowa została zmodyfikowana `ICalculatorSession` jako kontrakt, aby zezwolić na wykonywanie zestawu operacji przy zachowaniu uruchomionego wyniku. `ICalculator`</span><span class="sxs-lookup"><span data-stu-id="a0435-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="a0435-128">Usługa zachowuje stan przy użyciu funkcji dla każdego klienta, jako że wiele operacji usługi jest wywoływanych w celu wykonania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="a0435-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="a0435-129">Klient może pobrać bieżący wynik, wywołując `Result` i może wyczyścić wynik do zera przez wywołanie metody. `Clear`</span><span class="sxs-lookup"><span data-stu-id="a0435-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="a0435-130">Usługa używa sesji ASP.NET do przechowywania wyników dla każdej sesji klienta.</span><span class="sxs-lookup"><span data-stu-id="a0435-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="a0435-131">Dzięki temu usługa może zachować wynik działania dla każdego klienta w wielu wywołaniach do usługi.</span><span class="sxs-lookup"><span data-stu-id="a0435-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0435-132">Stan sesji ASP.NET i sesje WCF są bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="a0435-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="a0435-133">Aby uzyskać szczegółowe informacje na temat sesji WCF, zobacz temat [sesja](../../../../docs/framework/wcf/samples/session.md) .</span><span class="sxs-lookup"><span data-stu-id="a0435-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="a0435-134">Usługa ma zależność Intimate na stanie sesji ASP.NET i wymaga trybu zgodności ASP.NET w celu poprawnego działania.</span><span class="sxs-lookup"><span data-stu-id="a0435-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="a0435-135">Te wymagania są wyrażane w sposób deklaratywny `AspNetCompatibilityRequirements` przez zastosowanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a0435-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```csharp  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```
  
 <span data-ttu-id="a0435-136">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="a0435-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a0435-137">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="a0435-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a0435-138">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a0435-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a0435-139">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0435-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a0435-140">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0435-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a0435-141">Po skompilowaniu rozwiązania Uruchom polecenie Setup. bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a0435-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="a0435-142">Katalog ServiceModelSamples powinien teraz pojawić się jako aplikacja usług IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="a0435-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>  
  
4. <span data-ttu-id="a0435-143">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0435-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0435-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0435-144">See also</span></span>

- [<span data-ttu-id="a0435-145">Przykłady hostingu i trwałości usługi AppFabric</span><span class="sxs-lookup"><span data-stu-id="a0435-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
