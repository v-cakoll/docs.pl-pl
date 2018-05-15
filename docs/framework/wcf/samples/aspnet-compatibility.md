---
title: Zgodność platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: f621a3f13fafee67a015d463898a10aaf9104008
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="4797d-102">Zgodność platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4797d-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="4797d-103">W tym przykładzie pokazano, jak włączyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności w systemie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4797d-103">This sample demonstrates how to enable [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4797d-104">Usługi uruchomione [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności uczestniczyć w pełni [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji potoku i może wykonywać użycie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji, takich jak autoryzacja pliku lub adres URL, stan sesji i <xref:System.Web.HttpContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="4797d-104">Services running in [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode participate fully in the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application pipeline and can make use of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="4797d-105"><xref:System.Web.HttpContext> Klasy zezwala na dostęp do plików cookie sesji i innych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji.</span><span class="sxs-lookup"><span data-stu-id="4797d-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features.</span></span> <span data-ttu-id="4797d-106">Ten tryb wymaga powiązania korzystać z transportu HTTP i musi być obsługiwana przez usługę w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="4797d-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="4797d-107">W tym przykładzie klient jest aplikacji konsoli (plik wykonywalny), a usługa jest obsługiwana w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="4797d-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4797d-108">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4797d-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4797d-109">W tym przykładzie wymaga [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] puli aplikacji, aby można było uruchomić.</span><span class="sxs-lookup"><span data-stu-id="4797d-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="4797d-110">Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślnej puli aplikacji, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="4797d-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  
>   
>  1.  <span data-ttu-id="4797d-111">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="4797d-111">Open **Control Panel**.</span></span>  <span data-ttu-id="4797d-112">Otwórz **narzędzia administracyjne** apletu w obszarze **System i zabezpieczenia** nagłówka.</span><span class="sxs-lookup"><span data-stu-id="4797d-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="4797d-113">Otwórz **Internet Information Services (IIS) Manager** apletu.</span><span class="sxs-lookup"><span data-stu-id="4797d-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  
> 2.  <span data-ttu-id="4797d-114">Rozwiń element treeview w **połączeń** okienka.</span><span class="sxs-lookup"><span data-stu-id="4797d-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="4797d-115">Wybierz **pul aplikacji** węzła.</span><span class="sxs-lookup"><span data-stu-id="4797d-115">Select the **Application Pools** node.</span></span>  
> 3.  <span data-ttu-id="4797d-116">Aby ustawić domyślnej puli aplikacji do użycia [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (co może spowodować problemy niezgodności z istniejących lokacji,) kliknij prawym przyciskiem myszy **domyślna pula aplikacji** elementu listy, a następnie wybierz **podstawowych ustawień...** .</span><span class="sxs-lookup"><span data-stu-id="4797d-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="4797d-117">Ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="4797d-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  
> 4.  <span data-ttu-id="4797d-118">Aby utworzyć nową pulę aplikacji, która używa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (Aby zachować zgodność z innych aplikacji), kliknij prawym przyciskiem myszy **pul aplikacji** a następnie wybierz węzeł **Dodawanie puli aplikacji...** .</span><span class="sxs-lookup"><span data-stu-id="4797d-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="4797d-119">Nazwa nowej puli aplikacji, a następnie ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="4797d-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="4797d-120">Po uruchomić Instalatora kroków poniżej, kliknij prawym przyciskiem myszy **ServiceModelSamples** aplikacji i wybierz **aplikacji Zarządzanie**, **Zaawansowane ustawienia...** .</span><span class="sxs-lookup"><span data-stu-id="4797d-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="4797d-121">Ustaw **puli aplikacji** do nowej puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4797d-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4797d-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4797d-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4797d-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4797d-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4797d-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4797d-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4797d-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4797d-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="4797d-126">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="4797d-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="4797d-127">`ICalculator` Kontraktu został zmodyfikowany jako `ICalculatorSession` kontraktu umożliwiają zestaw operacji wykonywanych przy zachowaniu uruchomionych wynik.</span><span class="sxs-lookup"><span data-stu-id="4797d-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```  
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
  
 <span data-ttu-id="4797d-128">Usługa zachowuje swój stan, korzystanie z funkcji, dla każdego klienta, jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="4797d-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="4797d-129">Klient może pobrać bieżący wynik przez wywołanie metody `Result` i wyczyścić wynik, który ma wartość zero, wywołując `Clear`.</span><span class="sxs-lookup"><span data-stu-id="4797d-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="4797d-130">Używane przez usługę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesji, aby przechowywać wynik dla każdej sesji klienta.</span><span class="sxs-lookup"><span data-stu-id="4797d-130">The service uses the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session to store the result for each client session.</span></span> <span data-ttu-id="4797d-131">Dzięki temu usługę, aby zachować wynik uruchomiony dla każdego klienta w całej wielu wywołań do usługi.</span><span class="sxs-lookup"><span data-stu-id="4797d-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="4797d-132"> Stan sesji i sesje WCF jest bardzo różnych rzeczy.</span><span class="sxs-lookup"><span data-stu-id="4797d-132"> session state and WCF sessions are very different things.</span></span>  <span data-ttu-id="4797d-133">Zobacz [sesji](../../../../docs/framework/wcf/samples/session.md) szczegółowe informacje dotyczące sesji WCF.</span><span class="sxs-lookup"><span data-stu-id="4797d-133">See the [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>  
  
 <span data-ttu-id="4797d-134">Usługa ma zależności jednorodnej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stan sesji i wymaga [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności, aby mógł działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="4797d-134">The service has an intimate dependency on [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and requires [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compatibility mode to function correctly.</span></span> <span data-ttu-id="4797d-135">Te wymagania są wyrażane deklaratywnie przez zastosowanie `AspNetCompatibilityRequirements` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4797d-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```  
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
  
 <span data-ttu-id="4797d-136">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4797d-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4797d-137">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="4797d-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4797d-138">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="4797d-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4797d-139">Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4797d-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4797d-140">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4797d-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4797d-141">Po utworzeniu rozwiązania należy uruchomić pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4797d-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="4797d-142">Katalog ServiceModelSamples powinien zostać wyświetlony jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4797d-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="4797d-143">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4797d-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4797d-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4797d-144">See Also</span></span>  
 [<span data-ttu-id="4797d-145">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="4797d-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
