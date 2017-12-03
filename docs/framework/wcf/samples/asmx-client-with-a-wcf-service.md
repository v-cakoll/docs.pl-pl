---
title: "Klient ASMX z usługą WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f4c89e6382b5edd0ca295fde8f498fe97bdb64d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="2622e-102">Klient ASMX z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="2622e-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="2622e-103">W tym przykładzie pokazano, jak utworzyć przy użyciu usługi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i uzyskuje dostęp do usługi z innej[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, takich jak klient ASMX.</span><span class="sxs-lookup"><span data-stu-id="2622e-103">This sample demonstrates how to create a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and then access the service from a non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2622e-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2622e-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2622e-105">W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), obsługiwane przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="2622e-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="2622e-106">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="2622e-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2622e-107">Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (`Add`, `Subtract`, `Multiply`, i `Divide`).</span><span class="sxs-lookup"><span data-stu-id="2622e-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="2622e-108">Klient ASMX zgłasza żądań synchronicznych operacji matematycznych i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="2622e-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="2622e-109">Implementuje usługi `ICalculator` kontraktu zgodnie z definicją w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2622e-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
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
  
 <span data-ttu-id="2622e-110"><xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> mapowania typów CLR reprezentację XML.</span><span class="sxs-lookup"><span data-stu-id="2622e-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="2622e-111"><xref:System.Runtime.Serialization.DataContractSerializer> Inaczej niż XmlSerializer interpretuje niektóre reprezentacji XML.</span><span class="sxs-lookup"><span data-stu-id="2622e-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="2622e-112">Z systemem innym niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generatory serwera proxy, takich jak Wsdl.exe, generowanie bardziej użyteczne interfejsu, gdy jest używany element XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="2622e-112">Non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="2622e-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Jest stosowany do `ICalculator` interfejsu, aby upewnić się, że XmlSerializer służy do mapowania typów CLR XML.</span><span class="sxs-lookup"><span data-stu-id="2622e-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="2622e-114">Implementacji usługi jest obliczana i zwraca odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="2622e-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="2622e-115">Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji (Web.config).</span><span class="sxs-lookup"><span data-stu-id="2622e-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="2622e-116">Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2622e-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2622e-117">Usługa udostępnia punkt końcowy w bazowym adresie dostarczone przez hosta usługi Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="2622e-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="2622e-118">`binding` Atrybut ma ustawioną basicHttpBinding udostępniający komunikacji HTTP przy użyciu protokołu SOAP 1.1, który jest zgodny ze WS-I BasicProfile 1.1, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="2622e-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="2622e-119">Klient ASMX komunikuje się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przy użyciu typu serwera proxy, który jest generowany przez narzędzie Web Services Description Language (WSDL) (Wsdl.exe).</span><span class="sxs-lookup"><span data-stu-id="2622e-119">The ASMX client communicates with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="2622e-120">Typu serwera proxy znajduje się w pliku generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="2622e-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="2622e-121">Narzędzie WSDL pobiera metadane dla określonej usługi i generuje typu serwera proxy do użytku przez klienta do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="2622e-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="2622e-122">Domyślnie platformę nie ujawnia żadnych metadanych.</span><span class="sxs-lookup"><span data-stu-id="2622e-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="2622e-123">Do udostępnienia metadanych wymaganych do utworzenia serwera proxy, należy dodać [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) i ustawić jej `httpGetEnabled` atrybutu `True` jak pokazano w poniższej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2622e-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="2622e-124">Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="2622e-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="2622e-125">Za pomocą wygenerowanego typu serwera proxy, klient ma dostęp do danego punktu końcowego konfigurując odpowiednie adresy.</span><span class="sxs-lookup"><span data-stu-id="2622e-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="2622e-126">Klient korzysta z pliku konfiguracji (App.config) do określenia punktu końcowego do komunikowania się z.</span><span class="sxs-lookup"><span data-stu-id="2622e-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="2622e-127">Implementacja klienta tworzy wystąpienie klasy typizowanego serwera proxy do rozpoczęcia komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="2622e-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="2622e-128">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2622e-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2622e-129">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2622e-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2622e-130">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2622e-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2622e-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2622e-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2622e-132">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2622e-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2622e-133">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2622e-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2622e-134">przekazywanie i zwracający dane złożone typy Zobacz: [powiązania danych w kliencie formularzy systemu Windows](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [powiązania danych w kliencie systemu Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), i [powiązania danych w programie ASP.NET Klienta](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="2622e-134"> passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2622e-135">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2622e-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2622e-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2622e-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2622e-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2622e-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2622e-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2622e-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="2622e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2622e-139">See Also</span></span>
