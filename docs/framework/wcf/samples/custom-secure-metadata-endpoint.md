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
# <a name="custom-secure-metadata-endpoint"></a>Niestandardowy bezpieczny punkt końcowy metadanych
Niniejszy przykład pokazuje, jak wdrożyć usługę z punktu końcowego metadanych bezpieczny, który korzysta z jednego powiązania-metadata exchange i sposobie konfigurowania [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobrania metadane z punktu końcowego metadanych. Istnieją dwa powiązania dostarczane przez system dla punktów końcowych metadanych udostępniania: mexHttpBinding i mexHttpsBinding. mexHttpBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób, które nie są bezpieczne. mexHttpsBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób. Ten przykład ilustruje sposób uwidocznić punkt końcowy metadanych bezpiecznego przy użyciu <xref:System.ServiceModel.WSHttpBinding>. Należy to zrobić, jeśli chcesz zmienić ustawienia zabezpieczeń na powiązania, ale nie chcesz używać protokołu HTTPS. Jeśli używasz mexHttpsBinding punktu końcowego metadanych będą bezpieczne, ale nie ma sposobu na modyfikowanie ustawień powiązania.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Usługi w tym przykładzie ma dwa punkty końcowe. Punkt końcowy aplikacji służy `ICalculator` umowę na `WSHttpBinding` z `ReliableSession` włączone i `Message` zabezpieczeń przy użyciu certyfikatów. Używa również punkt końcowy metadanych `WSHttpBinding`, przy użyciu tych samych ustawień zabezpieczeń, ale bez `ReliableSession`. Poniżej przedstawiono istotne konfiguracji:  
  
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
  
 W wielu innych przykładów punkt końcowy metadanych używa domyślnej `mexHttpBinding`, który nie jest bezpieczne. W tym miejscu metadanych jest zabezpieczone przy użyciu `WSHttpBinding` z `Message` zabezpieczeń. Aby klienci metadanych do pobierania metadanych musi być skonfigurowany przy użyciu zgodnych powiązania. Niniejszy przykład pokazuje dwa takich klientów.  
  
 Pierwszy klient używa Svcutil.exe do pobierania metadanych i generowanie kodu klienta i konfiguracji w czasie projektowania. Ponieważ usługa korzysta z metadanych powiązanie inne niż domyślne, narzędzia Svcutil.exe muszą zostać skonfigurowane specjalnie tak, aby go pobrać metadane z usługi za pomocą tego powiązania.  
  
 Drugi klient używa `MetadataResolver` dynamicznie pobrać metadanych dla kontraktu znane i następnie wywołuje operacje na dynamicznie generowanym klienta.  
  
## <a name="svcutil-client"></a>Klient narzędzia svcutil  
 Podczas korzystania z wiązania domyślnego hosta z `IMetadataExchange` punkt końcowy, można uruchomić Svcutil.exe adres tego punktu końcowego:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 i jej działania. Ale w tym przykładzie serwer używa — do domyślnego punktu końcowego do obsługi metadanych. Dlatego Svcutil.exe musi być zobowiązany do używania poprawne powiązanie. Można to zrobić przy użyciu pliku Svcutil.exe.config.  
  
 Plik Svcutil.exe.config wygląda jak plik konfiguracji klienta normalny. Tylko nietypowe aspekty są nazwa punktu końcowego klienta i zamówienia:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Nazwa punktu końcowego musi być nazwa schematu adresu, gdzie znajduje się metadanych i kontraktu punktu końcowego musi być `IMetadataExchange`. W związku z tym, kiedy Svcutil.exe ma zostać uruchomiona przy użyciu wiersza polecenia takich jak następujące:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 szuka punktu końcowego o nazwie "http" i kontrakt `IMetadataExchange` skonfigurować powiązania i zachowanie programu exchange komunikacji z punktem końcowym metadanych. Pozostała część pliku Svcutil.exe.config w próbce określa Konfiguracja powiązania i zachowanie poświadczenia, aby dopasować konfiguracji serwera punktu końcowego metadanych.  
  
 Aby Svcutil.exe do pobrania konfiguracji w Svcutil.exe.config Svcutil.exe musi być w tym samym katalogu co plik konfiguracji. W rezultacie należy skopiować Svcutil.exe z lokalizacji instalacji do katalogu, który zawiera plik Svcutil.exe.config. Następnie z tego katalogu, uruchom następujące polecenie:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Wiodące ". \\"zapewnia, że uruchomieniu kopię Svcutil.exe w tym katalogu (taki, który ma odpowiedni Svcutil.exe.config).  
  
## <a name="metadataresolver-client"></a>Klient klasy MetadataResolver  
 Jeśli klient zna, kontrakt i jak komunikować się metadanych w czasie projektowania, klienta można dynamicznie znaleźć powiązania i adresu za pomocą punktów końcowych aplikacji `MetadataResolver`. Ten przykładowy klient pokazuje, w efekcie przedstawiająca sposób skonfigurować powiązania i poświadczenia używane przez `MetadataResolver` przez tworzenie i konfigurowanie `MetadataExchangeClient`.  
  
 Można określić obowiązkowo na te same informacje powiązania i certyfikatów, które pojawiło się w Svcutil.exe.config `MetadataExchangeClient`:  
  
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
  
 Za pomocą `mexClient` skonfigurowana, możemy wyliczyć kontraktów jesteśmy zainteresowani i `MetadataResolver` do pobrania listy punktów końcowych przy użyciu tych umów:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Na koniec możemy użyć informacji z tymi punktami końcowymi można zainicjować powiązania oraz adres `ChannelFactory` używany do tworzenia kanałów do komunikowania się z punktami końcowymi aplikacji.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Kluczowym punktem ten przykładowy klient jest zademonstrowanie, jeśli używasz `MetadataResolver`i należy określić powiązań niestandardowe lub zachowania komunikacji wymiany metadanych, możesz użyć `MetadataExchangeClient` określić te ustawienia niestandardowe.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu. Należy pamiętać, że Setup.bat przy użyciu narzędzia FindPrivateKey.exe, który jest zainstalowany, uruchamiając setupCertTool.bat z [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Uruchom aplikację klienta z \MetadataResolverClient\bin lub \SvcutilClient\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
3. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu dla próbki. Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.  
  
#### <a name="to-run-the-sample-across-machines"></a>Do uruchomienia przykładu na komputerach  
  
1. Na serwerze, uruchom `setup.bat service`. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
2. Na serwerze należy edytować plik Web.config, aby odzwierciedlały nową nazwę certyfikatu. Oznacza to, zmień `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu, aby w pełni kwalifikowana nazwa domeny komputera.  
  
3. Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
4. Na komputerze klienckim, należy uruchomić `setup.bat client`. Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
5. W pliku App.config `MetadataResolverClient` na komputerze klienckim, należy zmienić wartość adresu punktu końcowego mex, aby dopasować nowy adres usługi. Można to zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera. Wystąpienie "localhost" w pliku metadataResolverClient.cs można również zmienić na nową nazwę certyfikatu usługi (domeny w pełni kwalifikowaną nazwę serwera). Te same czynności wykonasz dla pliku App.config projektu SvcutilClient.  
  
6. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
7. Na komputerze klienckim, należy uruchomić `ImportServiceCert.bat`. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
8. Na serwerze, uruchom `ImportClientCert.bat`, to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
9. Na komputerze usługi kompilowania projektu usługi w programie Visual Studio, a następnie wybierz stronę pomocy w przeglądarce sieci web, aby sprawdzić, czy jest uruchomiona.  
  
10. Na komputerze klienckim należy uruchomić MetadataResolverClient lub SvcutilClient przy użyciu programu VS.  
  
    1. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
- Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na maszynach, pamiętaj wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
