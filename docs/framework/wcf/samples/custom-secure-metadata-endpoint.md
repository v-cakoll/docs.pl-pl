---
title: Niestandardowy bezpieczny punkt końcowy metadanych
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 92fa468caf331fadcd6cab0ab57b34858053c1b5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715448"
---
# <a name="custom-secure-metadata-endpoint"></a>Niestandardowy bezpieczny punkt końcowy metadanych
Ten przykład pokazuje, jak wdrożyć usługę z bezpiecznym punktem końcowym metadanych, który używa jednego z powiązań wymiany bez metadanych, oraz jak skonfigurować narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów, aby pobrać metadane z takiego punktu końcowego metadanych. Dostępne są dwa powiązania dostarczone przez system na potrzeby uwidaczniania punktów końcowych metadanych: mexHttpBinding i mexHttpsBinding. mexHttpBinding jest używany do uwidocznienia punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób niebezpieczny. mexHttpsBinding jest używany do udostępniania punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób. W tym przykładzie pokazano, jak uwidocznić bezpieczny punkt końcowy metadanych przy użyciu <xref:System.ServiceModel.WSHttpBinding>. Należy to zrobić, jeśli chcesz zmienić ustawienia zabezpieczeń dla powiązania, ale nie chcesz używać protokołu HTTPS. Jeśli używasz mexHttpsBinding, Twój punkt końcowy metadanych będzie zabezpieczony, ale nie ma możliwości modyfikacji ustawień powiązania.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>NDES  
 Usługa w tym przykładzie ma dwa punkty końcowe. Punkt końcowy aplikacji służy do `ICalculator` kontraktu na `WSHttpBinding` z włączonym `ReliableSession` i `Message` zabezpieczeniami przy użyciu certyfikatów. Punkt końcowy metadanych używa również `WSHttpBinding`z tymi samymi ustawieniami zabezpieczeń, ale bez `ReliableSession`. Oto odpowiednia konfiguracja:  
  
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
  
 W wielu innych przykładach punkt końcowy metadanych używa domyślnego `mexHttpBinding`, co nie jest bezpieczne. Metadane są zabezpieczane przy użyciu `WSHttpBinding` z zabezpieczeniami `Message`. Aby klienci metadanych mogli pobrać te metadane, muszą mieć skonfigurowane zgodne powiązania. Ten przykład pokazuje dwóch klientów.  
  
 Pierwszy klient używa programu Svcutil. exe, aby pobrać metadane i wygenerować kod i konfigurację klienta w czasie projektowania. Ponieważ usługa używa powiązania innego niż domyślne dla metadanych, narzędzie Svcutil. exe musi być skonfigurowane tak, aby można było pobrać metadane z usługi przy użyciu tego powiązania.  
  
 Drugi klient używa `MetadataResolver`, aby dynamicznie pobrać metadane dla znanego kontraktu, a następnie wywołać operacje na dynamicznie generowanym kliencie.  
  
## <a name="svcutil-client"></a>Klient Svcutil  
 W przypadku używania domyślnego powiązania do hostowania punktu końcowego `IMetadataExchange` można uruchomić Svcutil. exe z adresem tego punktu końcowego:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 i działa. Ale w tym przykładzie serwer używa innego niż domyślny punkt końcowy do hostowania metadanych. Dlatego należy wydać Svcutil. exe, aby użyć poprawnego powiązania. Można to zrobić za pomocą pliku Svcutil. exe. config.  
  
 Plik Svcutil. exe. config wygląda jak normalny plik konfiguracji klienta. Jedynymi nietypowymi aspektami są Nazwa i kontrakt punktu końcowego klienta:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Nazwa punktu końcowego musi być nazwą schematu adresu, na którym znajdują się metadane, a kontrakt punktu końcowego musi być `IMetadataExchange`. W związku z tym, gdy program Svcutil. exe jest uruchamiany z wiersza polecenia, takiego jak:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 szuka punktu końcowego o nazwie "http" i kontraktu `IMetadataExchange`, aby skonfigurować powiązanie i zachowanie wymiany komunikacji z punktem końcowym metadanych. Pozostała część pliku Svcutil. exe. config w przykładzie określa konfigurację powiązania i poświadczenia zachowania w celu dopasowania konfiguracji serwera punktu końcowego metadanych.  
  
 Aby program Svcutil. exe mógł pobrać konfigurację w pliku Svcutil. exe. config, Svcutil. exe musi znajdować się w tym samym katalogu, w którym znajduje się plik konfiguracji. W związku z tym należy skopiować Svcutil. exe z lokalizacji instalacji do katalogu, który zawiera plik Svcutil. exe. config. Następnie z tego katalogu Uruchom następujące polecenie:  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Wiodąca ".\\"zapewnia, że jest uruchamiana kopia Svcutil. exe w tym katalogu (która ma odpowiednie Svcutil. exe. config).  
  
## <a name="metadataresolver-client"></a>Klient klasy MetadataResolver  
 Jeśli Klient zna umowę i jak komunikować się z metadanymi w czasie projektowania, klient może dynamicznie sprawdzić powiązania i adres punktów końcowych aplikacji przy użyciu `MetadataResolver`. Ten przykładowy klient pokazuje, jak skonfigurować powiązanie i poświadczenia używane przez `MetadataResolver` przez utworzenie i skonfigurowanie `MetadataExchangeClient`.  
  
 Te same informacje o powiązaniu i certyfikacie, które pojawiły się w Svcutil. exe. config, można bezwzględnie określić na `MetadataExchangeClient`:  
  
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
  
 W przypadku skonfigurowania `mexClient` można wyliczyć kontrakty, których szukasz, i użyć `MetadataResolver` do pobrania listy punktów końcowych z tymi umowami:  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Wreszcie możemy użyć informacji z tych punktów końcowych w celu zainicjowania powiązania i adresu `ChannelFactory` używanego do tworzenia kanałów w celu komunikowania się z punktami końcowymi aplikacji.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Najważniejszym punktem tego przykładowego klienta jest zaprezentowanie, że jeśli używasz `MetadataResolver`i musisz określić niestandardowe powiązania lub zachowania dla komunikacji z wymianą metadanych, możesz użyć `MetadataExchangeClient`, aby określić te ustawienia niestandardowe.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Uruchom setup. bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu. Należy pamiętać, że plik Setup. bat używa narzędzia FindPrivateKey. exe, które jest instalowane przez uruchomienie setupCertTool. bat z procedury konfiguracji jednokrotnej [dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Uruchom aplikację kliencką z \MetadataResolverClient\bin lub \SvcutilClient\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
3. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Usuń certyfikaty, uruchamiając Oczyść. bat po zakończeniu korzystania z przykładu. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
#### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na wielu maszynach  
  
1. Na serwerze programu Uruchom `setup.bat service`. Uruchomienie `setup.bat` z argumentem `service` tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny maszyny i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
2. Na serwerze programu Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu. Oznacza to, że należy zmienić atrybut `findValue` w elemencie [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) na w pełni kwalifikowaną nazwę domeny komputera.  
  
3. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
4. Na kliencie Uruchom `setup.bat client`. Uruchomienie `setup.bat` z argumentem `client` tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.  
  
5. W pliku App. config `MetadataResolverClient` na komputerze klienckim Zmień wartość adresu punktu końcowego MEX, aby odpowiadała nowemu adresowi usługi. Można to zrobić, zastępując localhost nazwą domeny, w której jest w pełni kwalifikowana. Zmień również wystąpienie "localhost" w pliku metadataResolverClient.cs na nazwę nowego certyfikatu usługi (w pełni kwalifikowana nazwa domeny serwera). Wykonaj tę samą czynność dla pliku App. config projektu SvcutilClient.  
  
6. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.  
  
7. Na kliencie Uruchom `ImportServiceCert.bat`. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
8. Na serwerze programu Uruchom `ImportClientCert.bat`, czyli importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.  
  
9. Na maszynie usługi Skompiluj projekt usługi w programie Visual Studio i wybierz stronę pomocy w przeglądarce sieci Web, aby sprawdzić, czy jest uruchomiona.  
  
10. Na komputerze klienckim uruchom MetadataResolverClient lub SvcutilClient z programu VS.  
  
    1. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między maszynami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między maszynami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
