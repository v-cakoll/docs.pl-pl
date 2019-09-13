---
title: Niestandardowy bezpieczny punkt końcowy metadanych
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 32e6e0238637f9c2ef6814ace35ccb0b78110b60
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928681"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="3bed8-102">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="3bed8-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="3bed8-103">Ten przykład pokazuje, jak wdrożyć usługę z bezpiecznym punktem końcowym metadanych, który używa jednego z powiązań wymiany bez metadanych, oraz jak skonfigurować narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów, aby pobrać metadane z takich punkt końcowy metadanych.</span><span class="sxs-lookup"><span data-stu-id="3bed8-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="3bed8-104">Dostępne są dwa powiązania dostarczone przez system na potrzeby uwidaczniania punktów końcowych metadanych: mexHttpBinding i mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="3bed8-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="3bed8-105">mexHttpBinding jest używany do uwidocznienia punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="3bed8-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="3bed8-106">mexHttpsBinding jest używany do udostępniania punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="3bed8-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="3bed8-107">W tym przykładzie pokazano, <xref:System.ServiceModel.WSHttpBinding>jak uwidocznić bezpieczny punkt końcowy metadanych przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="3bed8-108">Należy to zrobić, jeśli chcesz zmienić ustawienia zabezpieczeń dla powiązania, ale nie chcesz używać protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3bed8-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="3bed8-109">Jeśli używasz mexHttpsBinding, Twój punkt końcowy metadanych będzie zabezpieczony, ale nie ma możliwości modyfikacji ustawień powiązania.</span><span class="sxs-lookup"><span data-stu-id="3bed8-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bed8-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="3bed8-111">Usługa</span><span class="sxs-lookup"><span data-stu-id="3bed8-111">Service</span></span>  
 <span data-ttu-id="3bed8-112">Usługa w tym przykładzie ma dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="3bed8-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="3bed8-113">Punkt końcowy aplikacji `ICalculator` obsługuje kontrakt `WSHttpBinding` z `ReliableSession` włączonym i `Message` zabezpieczeniami przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="3bed8-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="3bed8-114">Punkt końcowy metadanych używa `WSHttpBinding`również z tymi samymi ustawieniami zabezpieczeń, ale z opcją No. `ReliableSession`</span><span class="sxs-lookup"><span data-stu-id="3bed8-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="3bed8-115">Oto odpowiednia konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="3bed8-115">Here is the relevant configuration:</span></span>  
  
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
  
 <span data-ttu-id="3bed8-116">W wielu innych przykładach punkt końcowy metadanych używa domyślnego `mexHttpBinding`, co nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="3bed8-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="3bed8-117">W tym miejscu metadane są zabezpieczone `WSHttpBinding` przy `Message` użyciu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3bed8-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="3bed8-118">Aby klienci metadanych mogli pobrać te metadane, muszą mieć skonfigurowane zgodne powiązania.</span><span class="sxs-lookup"><span data-stu-id="3bed8-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="3bed8-119">Ten przykład pokazuje dwóch klientów.</span><span class="sxs-lookup"><span data-stu-id="3bed8-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="3bed8-120">Pierwszy klient używa programu Svcutil. exe, aby pobrać metadane i wygenerować kod i konfigurację klienta w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="3bed8-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="3bed8-121">Ponieważ usługa używa powiązania innego niż domyślne dla metadanych, narzędzie Svcutil. exe musi być skonfigurowane tak, aby można było pobrać metadane z usługi przy użyciu tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3bed8-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="3bed8-122">Drugi klient używa programu `MetadataResolver` do dynamicznego pobierania metadanych znanego kontraktu, a następnie wywoływania operacji na dynamicznie generowanym kliencie.</span><span class="sxs-lookup"><span data-stu-id="3bed8-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="3bed8-123">Klient Svcutil</span><span class="sxs-lookup"><span data-stu-id="3bed8-123">Svcutil client</span></span>  
 <span data-ttu-id="3bed8-124">Korzystając z domyślnego powiązania do hostowania `IMetadataExchange` punktu końcowego, można uruchomić Svcutil. exe z adresem tego punktu końcowego:</span><span class="sxs-lookup"><span data-stu-id="3bed8-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3bed8-125">i działa.</span><span class="sxs-lookup"><span data-stu-id="3bed8-125">and it works.</span></span> <span data-ttu-id="3bed8-126">Ale w tym przykładzie serwer używa innego niż domyślny punkt końcowy do hostowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="3bed8-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="3bed8-127">Dlatego należy wydać Svcutil. exe, aby użyć poprawnego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3bed8-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="3bed8-128">Można to zrobić za pomocą pliku Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="3bed8-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="3bed8-129">Plik Svcutil. exe. config wygląda jak normalny plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="3bed8-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="3bed8-130">Jedynymi nietypowymi aspektami są Nazwa i kontrakt punktu końcowego klienta:</span><span class="sxs-lookup"><span data-stu-id="3bed8-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="3bed8-131">Nazwa punktu końcowego musi być nazwą schematu adresu, na którym znajdują się metadane, i musi być `IMetadataExchange`kontraktem punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3bed8-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="3bed8-132">W związku z tym, gdy program Svcutil. exe jest uruchamiany z wiersza polecenia, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="3bed8-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3bed8-133">szuka punktu końcowego o nazwie "http" i kontraktu `IMetadataExchange` , aby skonfigurować powiązanie i zachowanie wymiany komunikacji z punktem końcowym metadanych.</span><span class="sxs-lookup"><span data-stu-id="3bed8-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="3bed8-134">Pozostała część pliku Svcutil. exe. config w przykładzie określa konfigurację powiązania i poświadczenia zachowania w celu dopasowania konfiguracji serwera punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="3bed8-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="3bed8-135">Aby program Svcutil. exe mógł pobrać konfigurację w pliku Svcutil. exe. config, Svcutil. exe musi znajdować się w tym samym katalogu, w którym znajduje się plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3bed8-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="3bed8-136">W związku z tym należy skopiować Svcutil. exe z lokalizacji instalacji do katalogu, który zawiera plik Svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="3bed8-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="3bed8-137">Następnie z tego katalogu Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="3bed8-137">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="3bed8-138">Wiodąca ". \\"zapewnia, że jest uruchamiana kopia Svcutil. exe w tym katalogu (która ma odpowiednie Svcutil. exe. config).</span><span class="sxs-lookup"><span data-stu-id="3bed8-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="3bed8-139">Klient klasy MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="3bed8-139">MetadataResolver client</span></span>  
 <span data-ttu-id="3bed8-140">Jeśli Klient zna umowę i jak komunikować się z metadanymi w czasie projektowania, klient może dynamicznie sprawdzić powiązania i adres punktów końcowych aplikacji przy użyciu `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="3bed8-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="3bed8-141">Ten przykładowy klient pokazuje, jak skonfigurować powiązanie i poświadczenia używane przez `MetadataResolver` tworzenie i `MetadataExchangeClient`Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="3bed8-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="3bed8-142">Te same informacje o powiązaniu i certyfikacie, które pojawiły się w Svcutil. exe. config, można `MetadataExchangeClient`określić w sposób niezależny od:</span><span class="sxs-lookup"><span data-stu-id="3bed8-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="3bed8-143">Dzięki skonfigurowaniu można wyliczyć kontrakty, których interesuje, i użyć `MetadataResolver` do pobrania listy punktów końcowych z tymi umowami: `mexClient`</span><span class="sxs-lookup"><span data-stu-id="3bed8-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="3bed8-144">Wreszcie możemy użyć informacji z tych punktów końcowych w celu zainicjowania powiązania i adresu `ChannelFactory` używanego do tworzenia kanałów w celu komunikowania się z punktami końcowymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bed8-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="3bed8-145">Najważniejszym punktem tego przykładowego klienta jest zaprezentowanie, że jeśli używasz programu `MetadataResolver`, i musisz określić niestandardowe powiązania lub zachowania dla komunikacji z wymianą metadanych, możesz `MetadataExchangeClient` użyć, aby określić te ustawienia niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="3bed8-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="3bed8-146">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="3bed8-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="3bed8-147">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bed8-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3bed8-148">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bed8-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="3bed8-149">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="3bed8-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="3bed8-150">Uruchom setup. bat z przykładowego folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3bed8-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="3bed8-151">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="3bed8-152">Należy pamiętać, że plik Setup. bat używa narzędzia FindPrivateKey. exe, które jest instalowane przez uruchomienie setupCertTool. bat z procedury konfiguracji jednokrotnej [dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3bed8-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3bed8-153">Uruchom aplikację kliencką z \MetadataResolverClient\bin lub \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="3bed8-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="3bed8-154">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="3bed8-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="3bed8-155">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3bed8-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="3bed8-156">Usuń certyfikaty, uruchamiając Oczyść. bat po zakończeniu korzystania z przykładu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="3bed8-157">Inne przykłady zabezpieczeń używają tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="3bed8-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="3bed8-158">Aby uruchomić przykład na wielu maszynach</span><span class="sxs-lookup"><span data-stu-id="3bed8-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="3bed8-159">Na serwerze uruchom `setup.bat service`polecenie.</span><span class="sxs-lookup"><span data-stu-id="3bed8-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="3bed8-160">`setup.bat` Uruchomienie`service` z argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny maszyny i eksportuje certyfikat usługi do pliku o nazwie Service. cer.</span><span class="sxs-lookup"><span data-stu-id="3bed8-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="3bed8-161">Na serwerze programu Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="3bed8-162">Oznacza to, że należy `findValue` zmienić atrybut [ \<w elemencie serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) na w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="3bed8-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="3bed8-163">Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="3bed8-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="3bed8-164">Na kliencie Uruchom `setup.bat client`polecenie.</span><span class="sxs-lookup"><span data-stu-id="3bed8-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="3bed8-165">`setup.bat` Uruchomienie`client` z argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.</span><span class="sxs-lookup"><span data-stu-id="3bed8-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="3bed8-166">W pliku `MetadataResolverClient` App. config na komputerze klienckim Zmień wartość adresu punktu końcowego MEX, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="3bed8-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="3bed8-167">Można to zrobić, zastępując localhost nazwą domeny, w której jest w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="3bed8-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="3bed8-168">Zmień również wystąpienie "localhost" w pliku metadataResolverClient.cs na nazwę nowego certyfikatu usługi (w pełni kwalifikowana nazwa domeny serwera).</span><span class="sxs-lookup"><span data-stu-id="3bed8-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="3bed8-169">Wykonaj tę samą czynność dla pliku App. config projektu SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="3bed8-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="3bed8-170">Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="3bed8-171">Na kliencie Uruchom `ImportServiceCert.bat`polecenie.</span><span class="sxs-lookup"><span data-stu-id="3bed8-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="3bed8-172">Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="3bed8-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="3bed8-173">Na serwerze programu uruchom `ImportClientCert.bat`program, który importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="3bed8-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="3bed8-174">Na maszynie usługi Skompiluj projekt usługi w programie Visual Studio i wybierz stronę pomocy w przeglądarce sieci Web, aby sprawdzić, czy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="3bed8-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="3bed8-175">Na komputerze klienckim uruchom MetadataResolverClient lub SvcutilClient z programu VS.</span><span class="sxs-lookup"><span data-stu-id="3bed8-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="3bed8-176">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3bed8-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3bed8-177">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="3bed8-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="3bed8-178">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3bed8-179">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między maszynami.</span><span class="sxs-lookup"><span data-stu-id="3bed8-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="3bed8-180">W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między maszynami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="3bed8-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3bed8-181">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="3bed8-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="3bed8-182">Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="3bed8-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3bed8-183">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3bed8-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3bed8-184">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3bed8-184">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3bed8-185">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3bed8-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3bed8-186">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3bed8-186">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
