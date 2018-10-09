---
title: Aktywowanie elementu NamedPipe
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 5f277d2c72822d8828355d3d728864bedb6dc4f4
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873365"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="2647b-102">Aktywowanie elementu NamedPipe</span><span class="sxs-lookup"><span data-stu-id="2647b-102">NamedPipe Activation</span></span>
<span data-ttu-id="2647b-103">Niniejszy przykład pokazuje usługi, używającej Windows Process Activation Service (WAS), aby aktywować usługę, która komunikuje się za pośrednictwem potoków nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="2647b-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="2647b-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i wymaga [!INCLUDE[wv](../../../../includes/wv-md.md)] do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="2647b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2647b-105">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2647b-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2647b-106">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2647b-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2647b-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2647b-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2647b-108">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2647b-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2647b-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2647b-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="2647b-110">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="2647b-110">Sample Details</span></span>  
 <span data-ttu-id="2647b-111">Przykład składa się z konsoli program kliencki (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez Windows Process Activation usług (WAS).</span><span class="sxs-lookup"><span data-stu-id="2647b-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="2647b-112">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2647b-112">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="2647b-113">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="2647b-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2647b-114">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia,) jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2647b-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="2647b-115">Klient wysyła żądań synchronicznych operacji matematycznych danego i implementacji usługi oblicza i zwraca odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="2647b-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>  
  
```  
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
  
 <span data-ttu-id="2647b-116">W przykładzie użyto zmodyfikowane `netNamedPipeBinding` powiązania z żadnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2647b-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="2647b-117">Powiązanie jest określona w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="2647b-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="2647b-118">Typ powiązania usługi jest określona w elemencie punktu końcowego `binding` atrybutu, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="2647b-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
 <span data-ttu-id="2647b-119">Jeśli chcesz użyć powiązania zabezpieczonej nazwany potok, zmianę trybu zabezpieczeń serwera z ustawieniem pożądanych zabezpieczeń i ponownie uruchom svcutil.exe na kliencie, aby uzyskać zaktualizowanego klienta z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2647b-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>  
  
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
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
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
  
 <span data-ttu-id="2647b-120">Informacje o punkcie końcowym klienta jest skonfigurowany, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2647b-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>  
  
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
            Each property is configured with the default value.   -->  
  
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
  
 <span data-ttu-id="2647b-121">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2647b-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2647b-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2647b-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2647b-123">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2647b-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2647b-124">Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="2647b-124">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)] <span data-ttu-id="2647b-125">jest wymagany do aktywacji WAS.</span><span class="sxs-lookup"><span data-stu-id="2647b-125"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="2647b-126">Upewnij się, kiedy została wykonana [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2647b-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="2647b-127">Ponadto należy zainstalować składniki Aktywacja bez HTTP programu WCF:</span><span class="sxs-lookup"><span data-stu-id="2647b-127">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="2647b-128">Z **Start** menu, wybierz **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2647b-128">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="2647b-129">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="2647b-129">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="2647b-130">Kliknij przycisk **włączyć składników Windows lub wyłączyć**.</span><span class="sxs-lookup"><span data-stu-id="2647b-130">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="2647b-131">Rozwiń **Microsoft .NET Framework 3.0** węzła i wyboru **Aktywacja bez HTTP programu Windows Communication Foundation** funkcji.</span><span class="sxs-lookup"><span data-stu-id="2647b-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="2647b-132">Skonfiguruj Windows Process Activation Service (WAS) do obsługi aktywacji nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="2647b-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>  
  
     <span data-ttu-id="2647b-133">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie AddNetPipeSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="2647b-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="2647b-134">Aby zapewnić obsługę aktywacji net.pipe, domyślna witryna sieci Web musi zostać powiązana z protokołem net.pipe.</span><span class="sxs-lookup"><span data-stu-id="2647b-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="2647b-135">Można to zrobić za pomocą appcmd.exe, który jest instalowany z zestawem narzędzi zarządzania usług IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="2647b-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="2647b-136">Z wiersza polecenia o podniesionych uprawnień (administrator) uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="2647b-136">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="2647b-137">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="2647b-137">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="2647b-138">To polecenie dodaje powiązanie witryny net.pipe do domyślnej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2647b-138">This command adds a net.pipe site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="2647b-139">Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.pipe, każdej aplikacji można włączyć obsługę net.pipe indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="2647b-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="2647b-140">Aby włączyć net.pipe aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2647b-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="2647b-141">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="2647b-141">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="2647b-142">To polecenie włącza aplikację /servicemodelsamples można uzyskać za pomocą zarówno `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="2647b-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>  
  
4.  <span data-ttu-id="2647b-143">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2647b-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="2647b-144">Usuń powiązanie witryny net.pipe, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="2647b-144">Remove the net.pipe site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="2647b-145">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie RemoveNetPipeSiteBinding.cmd znajduje się w katalogu próbki:</span><span class="sxs-lookup"><span data-stu-id="2647b-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="2647b-146">Usuń net.tcp z listy włączone protokoły, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2647b-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="2647b-147">To polecenie muszą zostać wprowadzone jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="2647b-147">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="2647b-148">Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2647b-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="2647b-149">To polecenie musi być wpisana w jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="2647b-149">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2647b-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2647b-150">See Also</span></span>  
 [<span data-ttu-id="2647b-151">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="2647b-151">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
