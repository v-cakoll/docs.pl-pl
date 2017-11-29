---
title: Aktywacja TCP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f02528828c3751b2f8e34bd7ebb8a1a789feeb2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tcp-activation"></a><span data-ttu-id="59c40-102">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="59c40-102">TCP Activation</span></span>
<span data-ttu-id="59c40-103">W przykładzie pokazano obsługującego usługę korzystającą z usługi aktywacji procesów systemu Windows (WAS) można aktywować usługi, która komunikuje się za pomocą protokołu net.tcp.</span><span class="sxs-lookup"><span data-stu-id="59c40-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="59c40-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="59c40-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59c40-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="59c40-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59c40-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="59c40-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="59c40-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="59c40-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="59c40-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="59c40-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59c40-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="59c40-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 <span data-ttu-id="59c40-110">Próbki składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez usługę WAS.</span><span class="sxs-lookup"><span data-stu-id="59c40-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="59c40-111">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="59c40-111">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="59c40-112">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="59c40-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="59c40-113">Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia), jak pokazano w poniższym kodzie próbki:</span><span class="sxs-lookup"><span data-stu-id="59c40-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="59c40-114">Implementacja usługi oblicza i zwraca wynik w odpowiednich:</span><span class="sxs-lookup"><span data-stu-id="59c40-114">The service implementation calculates and returns the appropriate result:</span></span>  
  
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
  
 <span data-ttu-id="59c40-115">W przykładzie użyto wariant net.tcp powiązanie o włączone udostępnianie portów TCP i zabezpieczeń wyłączone.</span><span class="sxs-lookup"><span data-stu-id="59c40-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="59c40-116">Jeśli chcesz użyć zabezpieczonych powiązanie TCP, Zmień tryb zabezpieczeń serwera na odpowiednie ustawienie i uruchom ponownie Svcutil.exe na kliencie, aby wygenerować plik konfiguracji aktualizacji klienta.</span><span class="sxs-lookup"><span data-stu-id="59c40-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>  
  
 <span data-ttu-id="59c40-117">Poniższy przykład przedstawia konfigurację usługi:</span><span class="sxs-lookup"><span data-stu-id="59c40-117">The following sample shows the configuration for the service:</span></span>  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
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
  
 <span data-ttu-id="59c40-118">Punkt końcowy klienta jest skonfigurowane, jak pokazano na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="59c40-118">The client's endpoint is configured as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="59c40-119">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="59c40-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="59c40-120">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="59c40-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59c40-121">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="59c40-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="59c40-122">Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="59c40-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="59c40-123">jest wymagany dla aktywacji WAS.</span><span class="sxs-lookup"><span data-stu-id="59c40-123"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="59c40-124">Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59c40-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="59c40-125">Ponadto należy zainstalować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składniki Aktywacja bez HTTP:</span><span class="sxs-lookup"><span data-stu-id="59c40-125">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="59c40-126">Z **Start** menu, wybierz **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="59c40-126">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="59c40-127">Wybierz **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="59c40-127">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="59c40-128">Kliknij przycisk **Włącz składniki systemu Windows lub wyłącz**.</span><span class="sxs-lookup"><span data-stu-id="59c40-128">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="59c40-129">Rozwiń węzeł **Microsoft .NET Framework 3.0** węzeł i wyboru **Aktywacja bez HTTP programu systemu Windows Communication Foundation** funkcji.</span><span class="sxs-lookup"><span data-stu-id="59c40-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="59c40-130">Skonfiguruj WAS do obsługi aktywacji TCP.</span><span class="sxs-lookup"><span data-stu-id="59c40-130">Configure WAS to support TCP activation.</span></span>  
  
     <span data-ttu-id="59c40-131">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie AddNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="59c40-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="59c40-132">Aby zapewnić obsługę aktywacji net.tcp, domyślnej witryny sieci Web musi zostać powiązana do portów net.tcp.</span><span class="sxs-lookup"><span data-stu-id="59c40-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="59c40-133">Można to zrobić przy użyciu Appcmd.exe, który jest instalowany z zestawu narzędzi zarządzania usługi Internet Information Services 7.0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="59c40-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="59c40-134">Z wiersza polecenia z uprawnieniami administratora na poziomie uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="59c40-134">From an administrator-level command prompt, run the following command:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  <span data-ttu-id="59c40-135">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="59c40-135">This command is a single line of text.</span></span> <span data-ttu-id="59c40-136">To polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolnej nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="59c40-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>  
  
    2.  <span data-ttu-id="59c40-137">Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="59c40-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="59c40-138">Aby włączyć net.tcp dla aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:</span><span class="sxs-lookup"><span data-stu-id="59c40-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="59c40-139">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="59c40-139">This command is a single line of text.</span></span> <span data-ttu-id="59c40-140">To polecenie włącza /servicemodelsamples aplikacji można uzyskać dostęp, używając http://localhost/servicemodelsamples i net.tcp://localhost/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="59c40-140">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="59c40-141">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59c40-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="59c40-142">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="59c40-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
     <span data-ttu-id="59c40-143">Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="59c40-143">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="59c40-144">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="59c40-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="59c40-145">Usuń net.tcp z listy włączonych protokołów, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:</span><span class="sxs-lookup"><span data-stu-id="59c40-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="59c40-146">To polecenie należy wprowadzić jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="59c40-146">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="59c40-147">Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:</span><span class="sxs-lookup"><span data-stu-id="59c40-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="59c40-148">To polecenie należy wpisać w jako pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="59c40-148">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c40-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59c40-149">See Also</span></span>  
 [<span data-ttu-id="59c40-150">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="59c40-150">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
