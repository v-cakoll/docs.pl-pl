---
title: "Zgodność platformy ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c8cf38e65bbc917720b1a1c5b604d81ca536c14
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="c37d3-102">Zgodność platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c37d3-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="c37d3-103">W tym przykładzie pokazano, jak włączyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c37d3-103">This sample demonstrates how to enable [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="c37d3-104">Usługi uruchomione [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności uczestniczyć w pełni [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji potoku i może wykonywać użycie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji, takich jak autoryzacja pliku lub adres URL, stan sesji i <xref:System.Web.HttpContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="c37d3-104">Services running in [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode participate fully in the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application pipeline and can make use of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="c37d3-105"><xref:System.Web.HttpContext> Klasy zezwala na dostęp do plików cookie sesji i innych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji.</span><span class="sxs-lookup"><span data-stu-id="c37d3-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features.</span></span> <span data-ttu-id="c37d3-106">Ten tryb wymaga powiązania korzystać z transportu HTTP i musi być obsługiwana przez usługę w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="c37d3-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="c37d3-107">W tym przykładzie klient jest aplikacji konsoli (plik wykonywalny), a usługa jest obsługiwana w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c37d3-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c37d3-108">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c37d3-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c37d3-109">W tym przykładzie wymaga [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] puli aplikacji, aby można było uruchomić.</span><span class="sxs-lookup"><span data-stu-id="c37d3-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="c37d3-110">Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślnej puli aplikacji, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="c37d3-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  
>   
>  1.  <span data-ttu-id="c37d3-111">Otwórz **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="c37d3-111">Open **Control Panel**.</span></span>  <span data-ttu-id="c37d3-112">Otwórz **narzędzia administracyjne** apletu w obszarze **System i zabezpieczenia** nagłówka.</span><span class="sxs-lookup"><span data-stu-id="c37d3-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="c37d3-113">Otwórz **Internet Information Services (IIS) Manager** apletu.</span><span class="sxs-lookup"><span data-stu-id="c37d3-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  
> 2.  <span data-ttu-id="c37d3-114">Rozwiń element treeview w **połączeń** okienka.</span><span class="sxs-lookup"><span data-stu-id="c37d3-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="c37d3-115">Wybierz **pul aplikacji** węzła.</span><span class="sxs-lookup"><span data-stu-id="c37d3-115">Select the **Application Pools** node.</span></span>  
> 3.  <span data-ttu-id="c37d3-116">Aby ustawić domyślnej puli aplikacji do użycia [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (co może spowodować problemy niezgodności z istniejących lokacji,) kliknij prawym przyciskiem myszy **domyślna pula aplikacji** elementu listy, a następnie wybierz **podstawowych ustawień...** .</span><span class="sxs-lookup"><span data-stu-id="c37d3-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="c37d3-117">Ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="c37d3-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  
> 4.  <span data-ttu-id="c37d3-118">Aby utworzyć nową pulę aplikacji, która używa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (Aby zachować zgodność z innych aplikacji), kliknij prawym przyciskiem myszy **pul aplikacji** a następnie wybierz węzeł **Dodawanie puli aplikacji...** .</span><span class="sxs-lookup"><span data-stu-id="c37d3-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="c37d3-119">Nazwa nowej puli aplikacji, a następnie ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="c37d3-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="c37d3-120">Po uruchomić Instalatora kroków poniżej, kliknij prawym przyciskiem myszy **ServiceModelSamples** aplikacji i wybierz **aplikacji Zarządzanie**, **Zaawansowane ustawienia...** .</span><span class="sxs-lookup"><span data-stu-id="c37d3-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="c37d3-121">Ustaw **puli aplikacji** do nowej puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c37d3-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c37d3-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c37d3-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c37d3-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c37d3-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c37d3-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c37d3-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c37d3-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c37d3-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="c37d3-126">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="c37d3-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="c37d3-127">`ICalculator` Kontraktu został zmodyfikowany jako `ICalculatorSession` kontraktu umożliwiają zestaw operacji wykonywanych przy zachowaniu uruchomionych wynik.</span><span class="sxs-lookup"><span data-stu-id="c37d3-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
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
  
 <span data-ttu-id="c37d3-128">Usługa zachowuje swój stan, korzystanie z funkcji, dla każdego klienta, jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="c37d3-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="c37d3-129">Klient może pobrać bieżący wynik przez wywołanie metody `Result` i wyczyścić wynik, który ma wartość zero, wywołując `Clear`.</span><span class="sxs-lookup"><span data-stu-id="c37d3-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="c37d3-130">Używane przez usługę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesji, aby przechowywać wynik dla każdej sesji klienta.</span><span class="sxs-lookup"><span data-stu-id="c37d3-130">The service uses the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session to store the result for each client session.</span></span> <span data-ttu-id="c37d3-131">Dzięki temu usługę, aby zachować wynik uruchomiony dla każdego klienta w całej wielu wywołań do usługi.</span><span class="sxs-lookup"><span data-stu-id="c37d3-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="c37d3-132">Stan sesji i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesje są bardzo różnych rzeczy.</span><span class="sxs-lookup"><span data-stu-id="c37d3-132"> session state and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions are very different things.</span></span>  <span data-ttu-id="c37d3-133">Zobacz [sesji](../../../../docs/framework/wcf/samples/session.md) szczegółowe informacje na temat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesji.</span><span class="sxs-lookup"><span data-stu-id="c37d3-133">See the [Session](../../../../docs/framework/wcf/samples/session.md) for details on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.</span></span>  
  
 <span data-ttu-id="c37d3-134">Usługa ma zależności jednorodnej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stan sesji i wymaga [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności, aby mógł działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c37d3-134">The service has an intimate dependency on [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and requires [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compatibility mode to function correctly.</span></span> <span data-ttu-id="c37d3-135">Te wymagania są wyrażane deklaratywnie przez zastosowanie `AspNetCompatibilityRequirements` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c37d3-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
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
  
 <span data-ttu-id="c37d3-136">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c37d3-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c37d3-137">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c37d3-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c37d3-138">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="c37d3-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c37d3-139">Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c37d3-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c37d3-140">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c37d3-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c37d3-141">Po utworzeniu rozwiązania należy uruchomić pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c37d3-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="c37d3-142">Katalog ServiceModelSamples powinien zostać wyświetlony jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c37d3-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="c37d3-143">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c37d3-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37d3-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c37d3-144">See Also</span></span>  
 [<span data-ttu-id="c37d3-145">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="c37d3-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
