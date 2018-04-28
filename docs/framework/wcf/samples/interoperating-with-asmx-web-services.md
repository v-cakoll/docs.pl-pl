---
title: Współdziałanie z usługami sieci Web ASMX
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa28637ad4ffdc2652c4c925208cd699134579a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="interoperating-with-asmx-web-services"></a><span data-ttu-id="7eccc-102">Współdziałanie z usługami sieci Web ASMX</span><span class="sxs-lookup"><span data-stu-id="7eccc-102">Interoperating with ASMX Web Services</span></span>
<span data-ttu-id="7eccc-103">W tym przykładzie pokazano, jak zintegrować [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji klienckiej z istniejącej usługi sieci Web ASMX.</span><span class="sxs-lookup"><span data-stu-id="7eccc-103">This sample demonstrates how to integrate a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application with an existing ASMX Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7eccc-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7eccc-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7eccc-105">W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), obsługiwane przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="7eccc-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7eccc-106">Usługa jest usługą sieci Web ASMX implementujący kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7eccc-106">The service is an ASMX Web Service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="7eccc-107">Usługa udostępnia operacji matematycznych (`Add`, `Subtract`, `Multiply`, i `Divide`).</span><span class="sxs-lookup"><span data-stu-id="7eccc-107">The service exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="7eccc-108">Klient wysyła żądań synchronicznych operacji matematycznych i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="7eccc-108">The client makes synchronous requests to a math operation and the service replies with the result.</span></span> <span data-ttu-id="7eccc-109">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7eccc-109">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="7eccc-110">Implementacja usługi sieci Web ASMX pokazano następujący przykładowy kod oblicza i zwraca wynik odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="7eccc-110">The ASMX Web service implementation shown in the following sample code calculates and returns the appropriate result.</span></span>  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 <span data-ttu-id="7eccc-111">Zgodnie z konfiguracją, usługi mogą być wyświetlane w http://localhost/servicemodelsamples/service.asmx przez klienta na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7eccc-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.asmx by a client on the same machine.</span></span> <span data-ttu-id="7eccc-112">Dla klientów na komputerach zdalnych do uzyskania dostępu do usługi należy określić w kwalifikowanej nazwy domeny zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="7eccc-112">For clients on remote machines to access the service, a qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="7eccc-113">Komunikacja odbywa się za pośrednictwem wygenerowanych przez klienta [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7eccc-113">Communication is done through a client generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="7eccc-114">Klient znajduje się w pliku generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="7eccc-114">The client is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="7eccc-115">Usługa ASMX musi być dostępny w celu generowania kodu serwera proxy, ponieważ jest używany do pobierania metadanych zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="7eccc-115">The ASMX service must be available to generate the proxy code, because it is used to retrieve the updated metadata.</span></span> <span data-ttu-id="7eccc-116">Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="7eccc-116">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 <span data-ttu-id="7eccc-117">Za pomocą wygenerowanego klienta, można uzyskać dostępu do punktu końcowego usługi, konfigurując odpowiednie adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="7eccc-117">By using the generated client, you can access a service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="7eccc-118">Jak usługa Klient korzysta z pliku konfiguracji (App.config) do określenia punktu końcowego do komunikowania się z.</span><span class="sxs-lookup"><span data-stu-id="7eccc-118">Like the service, the client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span> <span data-ttu-id="7eccc-119">Konfiguracja punktu końcowego klienta składa się z adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7eccc-119">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
   <endpoint   
      address="http://localhost/ServiceModelSamples/service.asmx"   
      binding="basicHttpBinding"   
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 <span data-ttu-id="7eccc-120">Implementacja klienta tworzy wystąpienie klasy wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="7eccc-120">The client implementation constructs an instance of the generated client.</span></span> <span data-ttu-id="7eccc-121">Następnie można wygenerowanego klienta do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="7eccc-121">The generated client can then be used to communicate with the service.</span></span>  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
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
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="7eccc-122">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7eccc-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7eccc-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7eccc-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7eccc-124">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="7eccc-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7eccc-125">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7eccc-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7eccc-126">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7eccc-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7eccc-127">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7eccc-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7eccc-128">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7eccc-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7eccc-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7eccc-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7eccc-130">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7eccc-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7eccc-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7eccc-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="7eccc-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7eccc-132">See Also</span></span>
