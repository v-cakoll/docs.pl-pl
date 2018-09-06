---
title: Zgodność platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: eeb09914fc90848c987127c789379549917063f6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800183"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="c0071-102">Zgodność platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0071-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="c0071-103">Niniejszy przykład pokazuje, jak włączyć tryb zgodności ASP.NET w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c0071-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c0071-104">Usługi działające w zgodność platformy ASP.NET, tryb uczestniczą w pełni potoku platformy ASP.NET w aplikacji i ułatwia korzystanie z funkcji programu ASP.NET, takich jak plik lub adres URL autoryzacji, stan sesji i <xref:System.Web.HttpContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="c0071-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="c0071-105"><xref:System.Web.HttpContext> Klasy zezwala na dostęp do plików cookie, sesje i inne funkcje platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c0071-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="c0071-106">Ten tryb wymaga powiązania użyj transportu HTTP i usługi muszą być hostowane w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="c0071-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="c0071-107">W tym przykładzie klient to aplikacja konsoli (plik wykonywalny), a usługa jest hostowana w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c0071-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0071-108">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c0071-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="c0071-109">Ten przykładowy skrypt wymaga [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] puli aplikacji, aby można było uruchomić.</span><span class="sxs-lookup"><span data-stu-id="c0071-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="c0071-110">Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślnej puli aplikacji, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="c0071-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1.  <span data-ttu-id="c0071-111">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="c0071-111">Open **Control Panel**.</span></span>  <span data-ttu-id="c0071-112">Otwórz **narzędzia administracyjne** apletu w obszarze **System i zabezpieczenia** nagłówka.</span><span class="sxs-lookup"><span data-stu-id="c0071-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="c0071-113">Otwórz **Internet Information Services (IIS) Manager** apletu.</span><span class="sxs-lookup"><span data-stu-id="c0071-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2.  <span data-ttu-id="c0071-114">Rozwiń węzeł treeview w **połączeń** okienka.</span><span class="sxs-lookup"><span data-stu-id="c0071-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="c0071-115">Wybierz **pul aplikacji** węzła.</span><span class="sxs-lookup"><span data-stu-id="c0071-115">Select the **Application Pools** node.</span></span>  

3.  <span data-ttu-id="c0071-116">Do ustawiania domyślnej puli aplikacji do użycia [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (która może powodować problemów niezgodność z istniejących witryn), kliknij prawym przyciskiem myszy **DefaultAppPool** elementu listy, a następnie wybierz pozycję **podstawowych ustawień...** .</span><span class="sxs-lookup"><span data-stu-id="c0071-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="c0071-117">Ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="c0071-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4.  <span data-ttu-id="c0071-118">Aby utworzyć nową pulę aplikacji, która używa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (w celu zachowania zgodności dla innych aplikacji), kliknij prawym przyciskiem myszy **pul aplikacji** a następnie wybierz węzeł **Dodawanie puli aplikacji...** .</span><span class="sxs-lookup"><span data-stu-id="c0071-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="c0071-119">Nadaj nazwę nowej puli aplikacji, a następnie ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="c0071-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="c0071-120">Po instalujący kroki poniżej, kliknij prawym przyciskiem myszy **ServiceModelSamples** aplikacji i wybierz **Zarządzanie aplikacją**, **ustawienia zaawansowane...** .</span><span class="sxs-lookup"><span data-stu-id="c0071-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="c0071-121">Ustaw **puli aplikacji** do nowej puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0071-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0071-122">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c0071-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c0071-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c0071-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c0071-124">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c0071-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c0071-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c0071-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="c0071-126">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="c0071-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="c0071-127">`ICalculator` Kontraktu została zmodyfikowana jako `ICalculatorSession` kontraktu zezwolić na zestaw operacji wykonywanych przy jednoczesnym zachowaniu wynik uruchomionych.</span><span class="sxs-lookup"><span data-stu-id="c0071-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
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
  
 <span data-ttu-id="c0071-128">Usługa zapewnia stanu, korzystanie z funkcji dla każdego klienta, jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="c0071-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="c0071-129">Klient może pobrać bieżący wynik, wywołując `Result` i wyczyścić wynik, który ma wartość zero, wywołując `Clear`.</span><span class="sxs-lookup"><span data-stu-id="c0071-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="c0071-130">Usługa używa sesji programu ASP.NET, aby przechować wynik dla każdej sesji klienta.</span><span class="sxs-lookup"><span data-stu-id="c0071-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="c0071-131">Dzięki temu usługa do obsługi uruchomionych wyników dla każdego klienta w wielu wywołań do usługi.</span><span class="sxs-lookup"><span data-stu-id="c0071-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0071-132">Stan sesji programu ASP.NET i WCF sesji są bardzo różnych rzeczy.</span><span class="sxs-lookup"><span data-stu-id="c0071-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="c0071-133">Zobacz [sesji](../../../../docs/framework/wcf/samples/session.md) szczegółowe informacje dotyczące sesji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c0071-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="c0071-134">Usługa ma zależność obsługi stanu sesji platformy ASP.NET i wymaga tryb zgodności ASP.NET, aby działo poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c0071-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="c0071-135">Te wymagania są wyrażone w sposób deklaratywny, stosując `AspNetCompatibilityRequirements` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c0071-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
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
  
 <span data-ttu-id="c0071-136">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c0071-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c0071-137">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c0071-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c0071-138">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c0071-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c0071-139">Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0071-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c0071-140">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0071-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c0071-141">Po rozwiązaniu został utworzony, uruchom Setup.bat jest, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0071-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="c0071-142">Katalog ServiceModelSamples teraz powinny się wyświetlać jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0071-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="c0071-143">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0071-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0071-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0071-144">See Also</span></span>  
 [<span data-ttu-id="c0071-145">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="c0071-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
