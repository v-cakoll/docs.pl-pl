---
title: Aktywowanie elementu NamedPipe
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 8d9a10b94c52514db611144352653b911d109056
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602469"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="3dfd5-102">Aktywowanie elementu NamedPipe</span><span class="sxs-lookup"><span data-stu-id="3dfd5-102">NamedPipe Activation</span></span>

<span data-ttu-id="3dfd5-103">W tym przykładzie pokazano, jak hostować usługę, która używa usługi aktywacji procesów systemu Windows (WAS) do aktywowania usługi, która komunikuje się z potokami nazw.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="3dfd5-104">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) i wymaga uruchomienia systemu Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-104">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="3dfd5-105">Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3dfd5-106">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3dfd5-107">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3dfd5-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3dfd5-108">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3dfd5-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="3dfd5-110">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="3dfd5-110">Sample Details</span></span>

<span data-ttu-id="3dfd5-111">Przykład składa się z programu konsoli klienta (. exe) i biblioteki usług (. dll) hostowanej w procesie roboczym aktywowanym przez usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="3dfd5-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="3dfd5-112">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="3dfd5-113">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="3dfd5-114">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie), jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

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

<span data-ttu-id="3dfd5-115">Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a implementacja usługi oblicza i zwraca odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

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

<span data-ttu-id="3dfd5-116">Przykład używa zmodyfikowanego `netNamedPipeBinding` powiązania bez zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="3dfd5-117">Powiązanie jest określone w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="3dfd5-118">Typ powiązania dla usługi jest określony w atrybucie elementu punktu końcowego `binding` , jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="3dfd5-119">Jeśli chcesz użyć bezpiecznego powiązania nazwanego potoku, Zmień tryb zabezpieczeń serwera na żądane ustawienie zabezpieczeń i ponownie uruchom program Svcutil. exe na kliencie, aby uzyskać zaktualizowany plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
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

<span data-ttu-id="3dfd5-120">Informacje o punkcie końcowym klienta są konfigurowane, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="3dfd5-121">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3dfd5-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3dfd5-123">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3dfd5-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3dfd5-124">Upewnij się, że usługi IIS 7,0 są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="3dfd5-125">Do przeprowadzenia aktywacji wymagane są usługi IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="3dfd5-126">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3dfd5-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="3dfd5-127">Ponadto należy zainstalować składniki aktywacji inne niż HTTP programu WCF:</span><span class="sxs-lookup"><span data-stu-id="3dfd5-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="3dfd5-128">Z menu **Start** wybierz pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="3dfd5-129">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="3dfd5-130">Kliknij pozycję **Włącz lub Wyłącz składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="3dfd5-131">Rozwiń węzeł **Microsoft .NET Framework 3,0** i Sprawdź funkcję **aktywacji Windows Communication Foundation niehttp** .</span><span class="sxs-lookup"><span data-stu-id="3dfd5-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="3dfd5-132">Skonfiguruj usługę aktywacji procesów systemu Windows (WAS) do obsługi aktywacji potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="3dfd5-133">Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie AddNetPipeSiteBinding. cmd znajdującym się w przykładowym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="3dfd5-134">Aby można było obsługiwać aktywację net. pipe, domyślna witryna sieci Web musi być najpierw powiązana z protokołem net. pipe.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="3dfd5-135">Można to zrobić za pomocą programu Appcmd. exe, który jest instalowany przy użyciu zestawu narzędzi do zarządzania usługami IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="3dfd5-136">W wierszu polecenia z podwyższonym poziomem uprawnień (Administrator) Uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="3dfd5-137">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-137">This command is a single line of text.</span></span>

        <span data-ttu-id="3dfd5-138">To polecenie dodaje powiązanie witryny net. pipe do domyślnej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="3dfd5-139">Mimo że wszystkie aplikacje w lokacji współużytkują wspólne powiązanie net. pipe, każda aplikacja może włączyć obsługę sieci net. pipe pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="3dfd5-140">Aby włączyć usługę net. pipe dla aplikacji/servicemodelsamples, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="3dfd5-141">To polecenie jest pojedynczym wierszem tekstu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-141">This command is a single line of text.</span></span>

        <span data-ttu-id="3dfd5-142">To polecenie umożliwia dostęp do aplikacji/servicemodelsamples przy użyciu obu `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="3dfd5-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="3dfd5-143">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3dfd5-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="3dfd5-144">Usuń powiązanie witryny net. pipe dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="3dfd5-145">Jako wygoda, następujące dwa kroki są zaimplementowane w pliku wsadowym o nazwie RemoveNetPipeSiteBinding. cmd, który znajduje się w przykładowym katalogu:</span><span class="sxs-lookup"><span data-stu-id="3dfd5-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="3dfd5-146">Usuń usługę net. TCP z listy włączonych protokołów, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="3dfd5-147">To polecenie musi zostać wprowadzone jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="3dfd5-148">Usuń powiązanie witryny net. TCP, uruchamiając następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="3dfd5-149">To polecenie musi być wpisane jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="3dfd5-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dfd5-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dfd5-150">See also</span></span>

- <span data-ttu-id="3dfd5-151">[Przykłady hostingu i trwałości usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3dfd5-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
