---
title: Aktywacja TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 3487d84a63b2838dc1b55fdf3f41b410fcfc2e63
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094881"
---
# <a name="tcp-activation"></a><span data-ttu-id="2e5f6-102">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="2e5f6-102">TCP Activation</span></span>

<span data-ttu-id="2e5f6-103">Ten przykład pokazuje hosting usługi, która korzysta z usług aktywacji procesów systemu Windows (WAS) w celu aktywowania usługi, która komunikuje się za pośrednictwem protokołu net. TCP.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="2e5f6-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2e5f6-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e5f6-106">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2e5f6-107">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="2e5f6-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2e5f6-108">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e5f6-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e5f6-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="2e5f6-110">Przykład składa się z programu konsolowego klienta (exe) i biblioteki usług (. dll) hostowanej w procesie roboczym aktywowanym przez program.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="2e5f6-111">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="2e5f6-112">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2e5f6-113">Umowa jest definiowana przez interfejs `ICalculator`, który uwidacznia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie), jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="2e5f6-114">Implementacja usługi oblicza i zwraca odpowiedni wynik:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-114">The service implementation calculates and returns the appropriate result:</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="2e5f6-115">W przykładzie zastosowano wariant powiązania net. TCP z włączonym udostępnianiem portów TCP i wyłączonym zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="2e5f6-116">Jeśli chcesz użyć bezpiecznego powiązania TCP, Zmień tryb zabezpieczeń serwera na żądane ustawienie i ponownie uruchom program Svcutil. exe na kliencie, aby wygenerować plik konfiguracji klienta aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="2e5f6-117">Poniższy przykład pokazuje konfigurację usługi:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="2e5f6-118">Punkt końcowy klienta jest skonfigurowany tak, jak pokazano w następującym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="2e5f6-119">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2e5f6-120">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e5f6-121">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="2e5f6-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2e5f6-122">Upewnij się, że usługi IIS 7,0 są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-122">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="2e5f6-123">Do przeprowadzenia aktywacji wymagane są usługi IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-123">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="2e5f6-124">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f6-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="2e5f6-125">Ponadto należy zainstalować składniki aktywacji inne niż HTTP programu WCF:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="2e5f6-126">Z menu **Start** wybierz pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="2e5f6-127">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="2e5f6-128">Kliknij pozycję **Włącz lub Wyłącz składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="2e5f6-129">Rozwiń węzeł **Microsoft .NET Framework 3,0** i Sprawdź funkcję **aktywacji Windows Communication Foundation niehttp** .</span><span class="sxs-lookup"><span data-stu-id="2e5f6-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="2e5f6-130">Konfiguracja programu miała obsługiwać aktywację protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="2e5f6-131">Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie AddNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="2e5f6-132">Aby można było obsługiwać aktywację net. TCP, domyślną witryną sieci Web należy najpierw powiązać z portem net. TCP.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="2e5f6-133">Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania Internet Information Services 7,0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="2e5f6-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="2e5f6-134">W wierszu polecenia na poziomie administratora uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="2e5f6-135">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-135">This command is a single line of text.</span></span> <span data-ttu-id="2e5f6-136">To polecenie dodaje powiązanie witryny net. TCP do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolną nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="2e5f6-137">Mimo że wszystkie aplikacje w lokacji współdzielą wspólne powiązanie net. TCP, każda aplikacja może włączać pojedynczą obsługę protokołu net. TCP.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="2e5f6-138">Aby włączyć usługę net. TCP dla aplikacji/servicemodelsamples, uruchom następujące polecenie w wierszu polecenia administratora:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="2e5f6-139">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-139">This command is a single line of text.</span></span> <span data-ttu-id="2e5f6-140">To polecenie umożliwia dostęp do aplikacji/servicemodelsamples przy użyciu obu `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="2e5f6-141">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f6-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="2e5f6-142">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f6-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="2e5f6-143">Usuń powiązanie witryny net. TCP dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="2e5f6-144">Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding. cmd znajdującym się w przykładowym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="2e5f6-145">Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w wierszu polecenia na poziomie administratora:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="2e5f6-146">To polecenie musi zostać wprowadzone jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="2e5f6-147">Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w wierszu polecenia na poziomie administratora:</span><span class="sxs-lookup"><span data-stu-id="2e5f6-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="2e5f6-148">To polecenie musi być wpisane jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="2e5f6-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e5f6-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e5f6-149">See also</span></span>

- <span data-ttu-id="2e5f6-150">[Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2e5f6-150">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
