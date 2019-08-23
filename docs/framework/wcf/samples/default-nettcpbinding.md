---
title: Domyślny element NetTcpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net profile TCP
ms.assetid: e8475fe6-0ecd-407a-8e7e-45860561bb74
ms.openlocfilehash: b0cccefc9ceb186a5278cc4cabbab58944bf44d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961784"
---
# <a name="default-nettcpbinding"></a><span data-ttu-id="4e482-102">Domyślny element NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="4e482-102">Default NetTcpBinding</span></span>
<span data-ttu-id="4e482-103">Ten przykład ilustruje użycie <xref:System.ServiceModel.NetTcpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="4e482-103">This sample demonstrates the use of the <xref:System.ServiceModel.NetTcpBinding> binding.</span></span> <span data-ttu-id="4e482-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="4e482-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="4e482-105">W tym przykładzie usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="4e482-105">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="4e482-106">Klientem i usługą są aplikacje konsolowe.</span><span class="sxs-lookup"><span data-stu-id="4e482-106">Both the client and service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e482-107">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4e482-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e482-108">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4e482-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e482-109">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="4e482-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e482-110">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4e482-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e482-111">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4e482-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\Default`  
  
 <span data-ttu-id="4e482-112">Powiązanie jest określone w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="4e482-112">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4e482-113">Typ powiązania jest określony w `binding` atrybucie [ \<elementu punktu końcowego >](../../configure-apps/file-schema/wcf/endpoint-element.md) , jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="4e482-113">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4e482-114">Poprzedni przykład pokazuje, jak skonfigurować punkt końcowy do używania `netTcpBinding` powiązania z ustawieniami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="4e482-114">The previous sample shows how to configure an endpoint to use the `netTcpBinding` binding with the default settings.</span></span> <span data-ttu-id="4e482-115">Jeśli chcesz skonfigurować `netTcpBinding` powiązanie i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="4e482-115">If you want to configure the `netTcpBinding` binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="4e482-116">Punkt końcowy musi odwoływać się do konfiguracji powiązania za pomocą `bindingConfiguration` nazwy z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="4e482-116">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="4e482-117">W tym przykładzie Konfiguracja powiązania ma nazwę `Binding1` i jest zdefiniowana, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="4e482-117">In this sample, the binding configuration is named `Binding1` and is defined as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4e482-118">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4e482-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4e482-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="4e482-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press ENTER to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e482-120">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="4e482-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e482-121">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="4e482-121">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="4e482-122">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e482-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="4e482-123">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e482-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4e482-124">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e482-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e482-125">Ponieważ serwer jest samoobsługowy, należy określić tożsamość w pliku App. config klienta, aby uruchomić przykład w konfiguracji dla wielu maszyn.</span><span class="sxs-lookup"><span data-stu-id="4e482-125">Because the server is self-hosted, you must specify an identity in the client's App.config file to run the sample in a cross-machine configuration.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name=""  
          address="net.tcp://servername:9000/servicemodelsamples/service"   
          binding="netTcpBinding"   
          contract="Microsoft.ServiceModel.Samples.ICalculator">  
            <identity>  
              <userPrincipalName value = "user_name@service_domain"/>  
            </identity>  
      </endpoint>  
    </client>  
    ```  
