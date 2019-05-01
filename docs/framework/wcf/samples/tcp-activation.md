---
title: Aktywacja TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 065c4706d0a52414c4abed85044ce06ad3efe35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007750"
---
# <a name="tcp-activation"></a><span data-ttu-id="e37c6-102">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="e37c6-102">TCP Activation</span></span>

<span data-ttu-id="e37c6-103">Niniejszy przykład pokazuje usługi, który używa usługi aktywacji procesów Windows (WAS), aby aktywować usługę, która komunikuje się za pośrednictwem protokołu net.tcp hosta.</span><span class="sxs-lookup"><span data-stu-id="e37c6-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="e37c6-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e37c6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e37c6-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e37c6-106">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e37c6-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e37c6-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e37c6-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e37c6-108">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e37c6-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e37c6-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="e37c6-110">Przykład składa się z konsoli program kliencki (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez WAS.</span><span class="sxs-lookup"><span data-stu-id="e37c6-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="e37c6-111">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e37c6-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="e37c6-112">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="e37c6-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="e37c6-113">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia,) jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e37c6-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

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

<span data-ttu-id="e37c6-114">Implementacja usługi oblicza i zwraca odpowiedni wynik:</span><span class="sxs-lookup"><span data-stu-id="e37c6-114">The service implementation calculates and returns the appropriate result:</span></span>

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

<span data-ttu-id="e37c6-115">W przykładzie użyto wariant net.tcp, powiązanie z włączone udostępnianie portów TCP i zabezpieczeń wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e37c6-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="e37c6-116">Jeśli chcesz używać bezpiecznego powiązania protokołu TCP, Zmień tryb zabezpieczeń serwera na odpowiednie ustawienie i Svcutil.exe Uruchom ponownie na kliencie, aby wygenerować plik konfiguracji aktualizacji klienta.</span><span class="sxs-lookup"><span data-stu-id="e37c6-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="e37c6-117">Poniższy przykład pokazuje konfiguracji dla usługi:</span><span class="sxs-lookup"><span data-stu-id="e37c6-117">The following sample shows the configuration for the service:</span></span>

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

<span data-ttu-id="e37c6-118">Punkt końcowy klienta został skonfigurowany, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e37c6-118">The client's endpoint is configured as shown in the following sample code:</span></span>

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

<span data-ttu-id="e37c6-119">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e37c6-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e37c6-120">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e37c6-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e37c6-121">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="e37c6-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e37c6-122">Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="e37c6-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)] <span data-ttu-id="e37c6-123">jest wymagany do aktywacji WAS.</span><span class="sxs-lookup"><span data-stu-id="e37c6-123">is required for WAS activation.</span></span>

2. <span data-ttu-id="e37c6-124">Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e37c6-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="e37c6-125">Ponadto należy zainstalować składniki Aktywacja bez HTTP programu WCF:</span><span class="sxs-lookup"><span data-stu-id="e37c6-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="e37c6-126">Z **Start** menu, wybierz **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="e37c6-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="e37c6-127">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="e37c6-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="e37c6-128">Kliknij przycisk **włączyć składników Windows lub wyłączyć**.</span><span class="sxs-lookup"><span data-stu-id="e37c6-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="e37c6-129">Rozwiń **Microsoft .NET Framework 3.0** węzła i wyboru **Aktywacja bez HTTP programu Windows Communication Foundation** funkcji.</span><span class="sxs-lookup"><span data-stu-id="e37c6-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="e37c6-130">Skonfiguruj WAS do obsługi aktywacji TCP.</span><span class="sxs-lookup"><span data-stu-id="e37c6-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="e37c6-131">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie AddNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="e37c6-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="e37c6-132">Aby zapewnić obsługę aktywacji net.tcp, domyślna witryna sieci Web musi zostać powiązana portów net.tcp.</span><span class="sxs-lookup"><span data-stu-id="e37c6-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="e37c6-133">Można to zrobić za pomocą Appcmd.exe, który jest instalowany z zestawem narzędzi zarządzania programu Internet Information Services 7.0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="e37c6-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="e37c6-134">Z wiersza polecenia z uprawnieniami administratora na poziomie uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e37c6-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="e37c6-135">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-135">This command is a single line of text.</span></span> <span data-ttu-id="e37c6-136">To polecenie dodaje powiązanie witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 przy użyciu dowolnej nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="e37c6-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="e37c6-137">Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="e37c6-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="e37c6-138">Aby włączyć net.tcp aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:</span><span class="sxs-lookup"><span data-stu-id="e37c6-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="e37c6-139">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-139">This command is a single line of text.</span></span> <span data-ttu-id="e37c6-140">To polecenie włącza aplikację /servicemodelsamples można uzyskać za pomocą zarówno `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="e37c6-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="e37c6-141">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e37c6-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="e37c6-142">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e37c6-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="e37c6-143">Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="e37c6-144">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="e37c6-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="e37c6-145">Usuń z listy włączone protokoły net.tcp, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:</span><span class="sxs-lookup"><span data-stu-id="e37c6-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="e37c6-146">To polecenie muszą zostać wprowadzone jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="e37c6-147">Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:</span><span class="sxs-lookup"><span data-stu-id="e37c6-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="e37c6-148">To polecenie musi być wpisana w jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="e37c6-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="e37c6-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e37c6-149">See also</span></span>

- [<span data-ttu-id="e37c6-150">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="e37c6-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
