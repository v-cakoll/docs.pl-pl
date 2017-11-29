---
title: "Domyślny element NetTcpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Net profile TCP
ms.assetid: e8475fe6-0ecd-407a-8e7e-45860561bb74
caps.latest.revision: "39"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1977bab08f35c8603776974a9e5266cbb140b4e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="default-nettcpbinding"></a><span data-ttu-id="b860c-102">Domyślny element NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="b860c-102">Default NetTcpBinding</span></span>
<span data-ttu-id="b860c-103">W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.NetTcpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="b860c-103">This sample demonstrates the use of the <xref:System.ServiceModel.NetTcpBinding> binding.</span></span> <span data-ttu-id="b860c-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="b860c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="b860c-105">W tym przykładzie usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="b860c-105">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="b860c-106">Klient i usługa są aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b860c-106">Both the client and service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b860c-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b860c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b860c-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b860c-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b860c-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b860c-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b860c-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b860c-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b860c-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b860c-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\Default`  
  
 <span data-ttu-id="b860c-112">Powiązanie jest określona w plikach konfiguracji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="b860c-112">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b860c-113">Typ powiązania jest określona w `binding` atrybutu [ \<punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="b860c-113">The binding type is specified in the `binding` attribute of the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b860c-114">Poprzedni przykład przedstawia sposób konfigurowania punktu końcowego użycia `netTcpBinding` powiązania z ustawieniami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="b860c-114">The previous sample shows how to configure an endpoint to use the `netTcpBinding` binding with the default settings.</span></span> <span data-ttu-id="b860c-115">Jeśli chcesz skonfigurować `netTcpBinding` powiązania i zmieniania jego ustawienia, należy zdefiniować konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="b860c-115">If you want to configure the `netTcpBinding` binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="b860c-116">Punkt końcowy musi odwoływać się Konfiguracja powiązania o nazwie z `bindingConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b860c-116">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="b860c-117">W tym przykładzie ma nazwę konfiguracji powiązania `Binding1` i została zdefiniowana, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="b860c-117">In this sample, the binding configuration is named `Binding1` and is defined as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="b860c-118">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="b860c-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b860c-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="b860c-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press ENTER to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b860c-120">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b860c-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b860c-121">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="b860c-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="b860c-122">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b860c-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="b860c-123">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b860c-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="b860c-124">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b860c-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b860c-125">Ponieważ serwer jest samodzielnie hostowana, należy określić tożsamości w pliku App.config klienta, aby uruchomić przykładowy w konfiguracji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="b860c-125">Because the server is self-hosted, you must specify an identity in the client's App.config file to run the sample in a cross-machine configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b860c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b860c-126">See Also</span></span>
