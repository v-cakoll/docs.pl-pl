---
title: Niestandardowy bezpieczny punkt końcowy metadanych
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: c835cfecab38a76f285767f918dfc082915ffcfc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990720"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="c6785-102">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="c6785-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="c6785-103">Niniejszy przykład pokazuje, jak wdrożyć usługę z punktu końcowego metadanych bezpieczny, który korzysta z jednego powiązania-metadata exchange i sposobie konfigurowania [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobrania metadane z punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="c6785-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="c6785-104">Istnieją dwa powiązania dostarczane przez system dla punktów końcowych metadanych udostępniania: mexHttpBinding i mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="c6785-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="c6785-105">mexHttpBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób, które nie są bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="c6785-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="c6785-106">mexHttpsBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="c6785-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="c6785-107">Ten przykład ilustruje sposób uwidocznić punkt końcowy metadanych bezpiecznego przy użyciu <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="c6785-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="c6785-108">Należy to zrobić, jeśli chcesz zmienić ustawienia zabezpieczeń na powiązania, ale nie chcesz używać protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c6785-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="c6785-109">Jeśli używasz mexHttpsBinding punktu końcowego metadanych będą bezpieczne, ale nie ma sposobu na modyfikowanie ustawień powiązania.</span><span class="sxs-lookup"><span data-stu-id="c6785-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6785-110">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c6785-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="c6785-111">Usługa</span><span class="sxs-lookup"><span data-stu-id="c6785-111">Service</span></span>  
 <span data-ttu-id="c6785-112">Usługi w tym przykładzie ma dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="c6785-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="c6785-113">Punkt końcowy aplikacji służy `ICalculator` umowę na `WSHttpBinding` z `ReliableSession` włączone i `Message` zabezpieczeń przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c6785-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="c6785-114">Używa również punkt końcowy metadanych `WSHttpBinding`, przy użyciu tych samych ustawień zabezpieczeń, ale bez `ReliableSession`.</span><span class="sxs-lookup"><span data-stu-id="c6785-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="c6785-115">Poniżej przedstawiono istotne konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="c6785-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="c6785-116">W wielu innych przykładów punkt końcowy metadanych używa domyślnej `mexHttpBinding`, który nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="c6785-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="c6785-117">W tym miejscu metadanych jest zabezpieczone przy użyciu `WSHttpBinding` z `Message` zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c6785-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="c6785-118">Aby klienci metadanych do pobierania metadanych musi być skonfigurowany przy użyciu zgodnych powiązania.</span><span class="sxs-lookup"><span data-stu-id="c6785-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="c6785-119">Niniejszy przykład pokazuje dwa takich klientów.</span><span class="sxs-lookup"><span data-stu-id="c6785-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="c6785-120">Pierwszy klient używa Svcutil.exe do pobierania metadanych i generowanie kodu klienta i konfiguracji w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="c6785-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="c6785-121">Ponieważ usługa korzysta z metadanych powiązanie inne niż domyślne, narzędzia Svcutil.exe muszą zostać skonfigurowane specjalnie tak, aby go pobrać metadane z usługi za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c6785-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="c6785-122">Drugi klient używa `MetadataResolver` dynamicznie pobrać metadanych dla kontraktu znane i następnie wywołuje operacje na dynamicznie generowanym klienta.</span><span class="sxs-lookup"><span data-stu-id="c6785-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="c6785-123">Klient narzędzia svcutil</span><span class="sxs-lookup"><span data-stu-id="c6785-123">Svcutil client</span></span>  
 <span data-ttu-id="c6785-124">Podczas korzystania z wiązania domyślnego hosta z `IMetadataExchange` punkt końcowy, można uruchomić Svcutil.exe adres tego punktu końcowego:</span><span class="sxs-lookup"><span data-stu-id="c6785-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="c6785-125">i jej działania.</span><span class="sxs-lookup"><span data-stu-id="c6785-125">and it works.</span></span> <span data-ttu-id="c6785-126">Ale w tym przykładzie serwer używa — do domyślnego punktu końcowego do obsługi metadanych.</span><span class="sxs-lookup"><span data-stu-id="c6785-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="c6785-127">Dlatego Svcutil.exe musi być zobowiązany do używania poprawne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="c6785-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="c6785-128">Można to zrobić przy użyciu pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="c6785-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="c6785-129">Plik Svcutil.exe.config wygląda jak plik konfiguracji klienta normalny.</span><span class="sxs-lookup"><span data-stu-id="c6785-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="c6785-130">Tylko nietypowe aspekty są nazwa punktu końcowego klienta i zamówienia:</span><span class="sxs-lookup"><span data-stu-id="c6785-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="c6785-131">Nazwa punktu końcowego musi być nazwa schematu adresu, gdzie znajduje się metadanych i kontraktu punktu końcowego musi być `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="c6785-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="c6785-132">W związku z tym, kiedy Svcutil.exe ma zostać uruchomiona przy użyciu wiersza polecenia takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="c6785-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="c6785-133">szuka punktu końcowego o nazwie "http" i kontrakt `IMetadataExchange` skonfigurować powiązania i zachowanie programu exchange komunikacji z punktem końcowym metadanych.</span><span class="sxs-lookup"><span data-stu-id="c6785-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="c6785-134">Pozostała część pliku Svcutil.exe.config w próbce określa Konfiguracja powiązania i zachowanie poświadczenia, aby dopasować konfiguracji serwera punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="c6785-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="c6785-135">Aby Svcutil.exe do pobrania konfiguracji w Svcutil.exe.config Svcutil.exe musi być w tym samym katalogu co plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c6785-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="c6785-136">W rezultacie należy skopiować Svcutil.exe z lokalizacji instalacji do katalogu, który zawiera plik Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="c6785-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="c6785-137">Następnie z tego katalogu, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c6785-137">Then from that directory, run the following command:</span></span>  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="c6785-138">Wiodące ". \\"zapewnia, że uruchomieniu kopię Svcutil.exe w tym katalogu (taki, który ma odpowiedni Svcutil.exe.config).</span><span class="sxs-lookup"><span data-stu-id="c6785-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="c6785-139">Klient klasy MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="c6785-139">MetadataResolver client</span></span>  
 <span data-ttu-id="c6785-140">Jeśli klient zna, kontrakt i jak komunikować się metadanych w czasie projektowania, klienta można dynamicznie znaleźć powiązania i adresu za pomocą punktów końcowych aplikacji `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="c6785-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="c6785-141">Ten przykładowy klient pokazuje, w efekcie przedstawiająca sposób skonfigurować powiązania i poświadczenia używane przez `MetadataResolver` przez tworzenie i konfigurowanie `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="c6785-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="c6785-142">Można określić obowiązkowo na te same informacje powiązania i certyfikatów, które pojawiło się w Svcutil.exe.config `MetadataExchangeClient`:</span><span class="sxs-lookup"><span data-stu-id="c6785-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="c6785-143">Za pomocą `mexClient` skonfigurowana, możemy wyliczyć kontraktów jesteśmy zainteresowani i `MetadataResolver` do pobrania listy punktów końcowych przy użyciu tych umów:</span><span class="sxs-lookup"><span data-stu-id="c6785-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="c6785-144">Na koniec możemy użyć informacji z tymi punktami końcowymi można zainicjować powiązania oraz adres `ChannelFactory` używany do tworzenia kanałów do komunikowania się z punktami końcowymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c6785-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="c6785-145">Kluczowym punktem ten przykładowy klient jest zademonstrowanie, jeśli używasz `MetadataResolver`i należy określić powiązań niestandardowe lub zachowania komunikacji wymiany metadanych, możesz użyć `MetadataExchangeClient` określić te ustawienia niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="c6785-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="c6785-146">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="c6785-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="c6785-147">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6785-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c6785-148">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6785-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="c6785-149">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="c6785-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="c6785-150">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="c6785-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c6785-151">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="c6785-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="c6785-152">Należy pamiętać, że Setup.bat przy użyciu narzędzia FindPrivateKey.exe, który jest zainstalowany, uruchamiając setupCertTool.bat z [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6785-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c6785-153">Uruchom aplikację klienta z \MetadataResolverClient\bin lub \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="c6785-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="c6785-154">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="c6785-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="c6785-155">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c6785-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="c6785-156">Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu dla próbki.</span><span class="sxs-lookup"><span data-stu-id="c6785-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="c6785-157">Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c6785-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="c6785-158">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="c6785-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="c6785-159">Na serwerze, uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="c6785-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="c6785-160">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="c6785-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="c6785-161">Na serwerze należy edytować plik Web.config, aby odzwierciedlały nową nazwę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c6785-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="c6785-162">Oznacza to, zmień `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu, aby w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="c6785-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="c6785-163">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="c6785-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="c6785-164">Na komputerze klienckim, należy uruchomić `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="c6785-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="c6785-165">Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="c6785-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="c6785-166">W pliku App.config `MetadataResolverClient` na komputerze klienckim, należy zmienić wartość adresu punktu końcowego mex, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="c6785-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="c6785-167">Można to zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="c6785-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="c6785-168">Wystąpienie "localhost" w pliku metadataResolverClient.cs można również zmienić na nową nazwę certyfikatu usługi (domeny w pełni kwalifikowaną nazwę serwera).</span><span class="sxs-lookup"><span data-stu-id="c6785-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="c6785-169">Te same czynności wykonasz dla pliku App.config projektu SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="c6785-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="c6785-170">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c6785-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="c6785-171">Na komputerze klienckim, należy uruchomić `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="c6785-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="c6785-172">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="c6785-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="c6785-173">Na serwerze, uruchom `ImportClientCert.bat`, to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="c6785-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="c6785-174">Na komputerze usługi kompilowania projektu usługi w programie Visual Studio, a następnie wybierz stronę pomocy w przeglądarce sieci web, aby sprawdzić, czy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="c6785-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="c6785-175">Na komputerze klienckim należy uruchomić MetadataResolverClient lub SvcutilClient przy użyciu programu VS.</span><span class="sxs-lookup"><span data-stu-id="c6785-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="c6785-176">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c6785-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c6785-177">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="c6785-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="c6785-178">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="c6785-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6785-179">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="c6785-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="c6785-180">Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na maszynach, pamiętaj wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="c6785-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c6785-181">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="c6785-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="c6785-182">Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c6785-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6785-183">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c6785-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6785-184">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c6785-184">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6785-185">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c6785-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6785-186">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c6785-186">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
