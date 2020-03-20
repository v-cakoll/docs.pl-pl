---
title: Niestandardowy bezpieczny punkt końcowy metadanych
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183847"
---
# <a name="custom-secure-metadata-endpoint"></a>Niestandardowy bezpieczny punkt końcowy metadanych
W tym przykładzie pokazano, jak zaimplementować usługę z bezpiecznym punktem końcowym metadanych, który używa jednego z powiązań wymiany nie metadanych i jak skonfigurować [Narzędzie narzędzia Metadanych ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobierania metadanych z takiego punktu końcowego metadanych. Istnieją dwa powiązania dostarczone przez system do udostępniania punktów końcowych metadanych: mexHttpBinding i mexHttpsBinding. mexHttpBinding jest używany do uwidaczniania punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób niezabezpieczony. mexHttpsBinding jest używany do uwidaczniania punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób. W tym przykładzie pokazano, jak udostępnić <xref:System.ServiceModel.WSHttpBinding>bezpieczny punkt końcowy metadanych przy użyciu . Należy to zrobić, gdy chcesz zmienić ustawienia zabezpieczeń dla powiązania, ale nie chcesz używać protokołu HTTPS. Jeśli używasz mexHttpsBinding punkt końcowy metadanych będzie bezpieczny, ale nie ma możliwości modyfikowania ustawień powiązania.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Usługa w tym przykładzie ma dwa punkty końcowe. Punkt końcowy aplikacji `ICalculator` obsługuje umowy `ReliableSession` na `Message` z włączonych `WSHttpBinding` i zabezpieczeń przy użyciu certyfikatów. Punkt końcowy metadanych `WSHttpBinding`używa również, z tymi `ReliableSession`samymi ustawieniami zabezpieczeń, ale bez . Oto odpowiednia konfiguracja:  
  
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
  
 W wielu innych przykładach punkt końcowy metadanych `mexHttpBinding`używa domyślnego , który nie jest bezpieczny. W tym miejscu metadane są zabezpieczone przy użyciu `WSHttpBinding` `Message` zabezpieczeń. Aby klienci metadanych mogli pobrać te metadane, muszą być skonfigurowani przy tym z pasującym powiązaniem. W tym przykładzie przedstawiono dwa takie klientów.  
  
 Pierwszy klient używa programu Svcutil.exe do pobierania metadanych i generowania kodu klienta i konfiguracji w czasie projektowania. Ponieważ usługa używa powiązania nie domyślne dla metadanych, narzędzie Svcutil.exe musi być specjalnie skonfigurowane, aby można było uzyskać metadane z usługi przy użyciu tego powiązania.  
  
 Drugi klient używa `MetadataResolver` do dynamicznego pobierania metadanych dla znanego kontraktu, a następnie wywoływania operacji na dynamicznie generowanym kliencie.  
  
## <a name="svcutil-client"></a>Klient Svcutil  
 Podczas korzystania z domyślnego `IMetadataExchange` powiązania do hosta punktu końcowego, można uruchomić Svcutil.exe z adresem tego punktu końcowego:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 i to działa. Jednak w tym przykładzie serwer używa nieobekonicznego punktu końcowego do hostowania metadanych. Więc Svcutil.exe musi być poinstruowany, aby użyć prawidłowego wiązania. Można to zrobić za pomocą pliku Svcutil.exe.config.  
  
 Plik Svcutil.exe.config wygląda jak zwykły plik konfiguracji klienta. Jedynymi nietypowymi aspektami są nazwa punktu końcowego klienta i kontrakt:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Nazwa punktu końcowego musi być nazwą schematu adresu, w którym znajdują się metadane, a kontrakt punktu końcowego musi być `IMetadataExchange`. W związku z tym, gdy program Svcutil.exe jest uruchamiany z wierszem polecenia, takim jak:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 szuka punktu końcowego o nazwie "http" i umowy, `IMetadataExchange` aby skonfigurować powiązanie i zachowanie wymiany komunikacji z punktem końcowym metadanych. Reszta pliku Svcutil.exe.config w przykładzie określa konfigurację powiązania i poświadczenia zachowania, aby dopasować konfigurację serwera punktu końcowego metadanych.  
  
 Aby program Svcutil.exe odebrał konfigurację w pliku Svcutil.exe.config, program Svcutil.exe musi znajdować się w tym samym katalogu co plik konfiguracyjny. W związku z tym należy skopiować plik Svcutil.exe z jego lokalizacji instalacji do katalogu zawierającego plik Svcutil.exe.config. Następnie z tego katalogu uruchom następujące polecenie:  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Wiodący ". \\" zapewnia, że kopia Svcutil.exe w tym katalogu (ten, który ma odpowiedni Svcutil.exe.config) jest uruchamiany.  
  
## <a name="metadataresolver-client"></a>MetadataSobraz klienta  
 Jeśli klient zna umowę i jak rozmawiać z metadanymi w czasie projektowania, klient może dynamicznie `MetadataResolver`znaleźć powiązania i adres punktów końcowych aplikacji za pomocą . Ten przykładowy klient pokazuje to, pokazując, jak skonfigurować `MetadataResolver` powiązania i poświadczenia `MetadataExchangeClient`używane przez utworzenie i skonfigurowanie pliku .  
  
 Te same informacje o powiązaniach i certyfikatach, które pojawiły się w pliku `MetadataExchangeClient`Svcutil.exe.config, można bezwzględnie określić na stronie:  
  
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
  
 Za `mexClient` pomocą skonfigurowanego możemy wyliczyć interesujące kontrakty, które `MetadataResolver` nas interesują, i użyć do pobrania listy punktów końcowych z tymi umowami:  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Na koniec możemy użyć informacji z tych punktów końcowych do zainicjowania powiązania i adresu `ChannelFactory` używanego do tworzenia kanałów do komunikowania się z punktami końcowymi aplikacji.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Kluczowym punktem tego przykładowego klienta jest wykazanie, że jeśli używasz `MetadataResolver`, i należy określić niestandardowe powiązania `MetadataExchangeClient` lub zachowania dla komunikacji wymiany metadanych, można użyć, aby określić te ustawienia niestandardowe.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i utworzyć próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Uruchom plik Setup.bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki. Należy zauważyć, że plik Setup.bat używa narzędzia FindPrivateKey.exe, które jest instalowane przez uruchomienie pliku setupCertTool.bat z [procedury jednorazowej instalacji dla przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Uruchom aplikację kliencką z \MetadataResolverClient\bin lub \SvcutilClient\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
3. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Usuń certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
#### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Na serwerze `setup.bat service`uruchom program . Uruchamianie `setup.bat` `service` z argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
2. Na serwerze edytuj plik Web.config, aby odzwierciedlić nową nazwę certyfikatu. Oznacza to, `findValue` że zmień atrybut w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element do w pełni kwalifikowanej nazwy domeny komputera.  
  
3. Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
4. Na kliencie `setup.bat client`uruchom program . Uruchamianie `setup.bat` `client` z argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
5. W pliku App.config `MetadataResolverClient` na komputerze klienckim zmień wartość adresu punktu końcowego mex, aby dopasować go do nowego adresu usługi. Można to zrobić, zastępując localhost w pełni kwalifikowaną nazwą domeny serwera. Zmień również występowanie "localhost" w pliku metadataResolverClient.cs na nową nazwę certyfikatu usługi (w pełni kwalifikowaną nazwę domeny serwera). Zrób to samo dla App.config projektu SvcutilClient.  
  
6. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
7. Na kliencie `ImportServiceCert.bat`uruchom program . Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.  
  
8. Na serwerze `ImportClientCert.bat`uruchom program Uruchom program Ta importuje certyfikat klienta z pliku Client.cer do magazynu LocalMachine — TrustedPeople.  
  
9. Na komputerze usługi skompiluj projekt usługi w programie Visual Studio i wybierz stronę pomocy w przeglądarce sieci Web, aby sprawdzić, czy jest uruchomiona.  
  
10. Na komputerze klienckim uruchom MetadataResolverClient lub SvcutilClient z vs.  
  
    1. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
    > [!NOTE]
    > Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli zostały uruchomione windows communication foundation (WCF) przykłady, które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w CurrentUser — TrustedPeople magazynu. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`użyć następującego polecenia: . Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
