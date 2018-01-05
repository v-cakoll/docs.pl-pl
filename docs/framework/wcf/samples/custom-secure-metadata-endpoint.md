---
title: "Niestandardowy bezpieczny punkt końcowy metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cad98ab0df372b19efcf102cce3f80e3f7b0632f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-secure-metadata-endpoint"></a>Niestandardowy bezpieczny punkt końcowy metadanych
Przykładzie pokazano, jak wdrożyć usługę z punktem końcowym metadanych bezpieczny, jednym z powiązań wymiany metadanych z systemem innym niż i konfigurowanie [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobrania metadane z punktu końcowego metadanych. Dostępne są dwa powiązania dostarczane przez system dla udostępnianie punkty końcowe metadanych: mexHttpBinding i mexHttpsBinding. mexHttpBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób, które nie są bezpieczne. mexHttpsBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób. W tym przykładzie przedstawiono sposób ujawniać punkt końcowy metadanych bezpiecznego przy użyciu <xref:System.ServiceModel.WSHttpBinding>. Czy chcesz to zrobić, jeśli chcesz zmienić ustawienia zabezpieczeń dla powiązania, ale nie chcesz używać protokołu HTTPS. Jeśli używasz mexHttpsBinding punktu końcowego metadanych będzie bezpieczna, ale nie istnieje sposób zmodyfikować ustawienia powiązania.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Usługi w tym przykładzie ma dwa punkty końcowe. Punkt końcowy aplikacji służy `ICalculator` kontraktu na `WSHttpBinding` z `ReliableSession` włączone i `Message` zabezpieczeń za pomocą certyfikatów. Punkt końcowy metadanych używa również `WSHttpBinding`, z tymi samymi ustawieniami zabezpieczeń, ale bez `ReliableSession`. Poniżej przedstawiono istotne konfiguracji:  
  
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
  
 W wielu innych próbek punktu końcowego metadanych używa domyślnej `mexHttpBinding`, która nie jest bezpieczne. W tym miejscu metadanych jest zabezpieczone przy użyciu `WSHttpBinding` z `Message` zabezpieczeń. Aby klienci metadanych można pobrać metadanych musi być skonfigurowany z pasującego powiązania. W tym przykładzie przedstawiono dwóch takich klientów.  
  
 Pierwszy klient używa Svcutil.exe do pobierania metadanych i generowanie kodu klienta i konfiguracji w czasie projektowania. Ponieważ usługa korzysta z metadanych powiązania innych niż domyślne, z narzędzia Svcutil.exe muszą zostać skonfigurowane specjalnie, aby ją pobrać metadanych usługi za pomocą tego powiązania.  
  
 Drugi klient używa `MetadataResolver` dynamicznie pobrać metadanych dla znanych kontraktu i następnie wywoływać operacje na dynamicznie generowanym klienta.  
  
## <a name="svcutil-client"></a>Svcutil klienta  
 Korzystając z powiązania domyślnego hosta z `IMetadataExchange` punkt końcowy, można uruchomić Svcutil.exe adres tego punktu końcowego:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 i działa. Jednak w tym przykładzie serwer używa punktu końcowego innych niż domyślne do obsługi metadanych. Dlatego Svcutil.exe musi być zalecane jest używanie poprawne powiązanie. Można to zrobić przy użyciu pliku Svcutil.exe.config.  
  
 Plik Svcutil.exe.config wygląda jak plik konfiguracji normalne klienta. Tylko nietypowe aspekty są nazwa punktu końcowego klienta i kontraktu:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Nazwa punktu końcowego musi być nazwą systemu adres, gdzie jest hostowana metadanych i kontraktu punktu końcowego musi być `IMetadataExchange`. W związku z tym, kiedy Svcutil.exe jest uruchamiana z wiersza polecenia takich jak następujące:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 wygląda na to dla punktu końcowego o nazwie "http" i kontraktu `IMetadataExchange` do konfigurowania wiązania i zachowanie programu exchange komunikacji z punktem końcowym metadanych. Pozostała część pliku Svcutil.exe.config w próbce określa Konfiguracja powiązania i zachowanie poświadczeń do dopasowania konfiguracji serwera punktu końcowego metadanych.  
  
 Aby Svcutil.exe do pobrania konfiguracji w Svcutil.exe.config Svcutil.exe musi być w tym samym katalogu co plik konfiguracji. W związku z tym należy skopiować Svcutil.exe z lokalizacji instalacji do katalogu zawierającego plik Svcutil.exe.config. Następnie uruchom następujące polecenie z tego katalogu:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Znaku ". \\"zapewnia, że kopia Svcutil.exe w tym katalogu (taki, który ma odpowiednie Svcutil.exe.config) jest uruchamiane.  
  
## <a name="metadataresolver-client"></a>MetadataResolver klienta  
 Jeśli klient zna umowy oraz sposób zwróć się do metadanych w czasie projektowania, klienta można dynamicznie znaleźć powiązanie i adres punktów końcowych aplikacji za pomocą `MetadataResolver`. Ten klient przykładowych pokazano, pokazujący sposób konfigurowania powiązania i poświadczenia używane przez `MetadataResolver` przez tworzenie i konfigurowanie `MetadataExchangeClient`.  
  
 Powiązanie i certyfikatu informacje, które znajdowały się w Svcutil.exe.config można określić imperatively na `MetadataExchangeClient`:  
  
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
  
 Z `mexClient` skonfigurowane, możemy wyliczyć kontrakty firma Microsoft planuje się i użyj `MetadataResolver` można pobrać listy punktów końcowych o tych umów:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Na koniec możemy użyć informacji z tych punktów końcowych zainicjować powiązania oraz adres `ChannelFactory` używany do tworzenia kanałów do komunikowania się z punktami końcowymi aplikacji.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Klucza punkt ten klient próbki jest wykazać, że jeśli używasz `MetadataResolver`i należy określić niestandardowe powiązania lub zachowania dla komunikacji wymiany metadanych, możesz użyć `MetadataExchangeClient` do określenia tych ustawień niestandardowych.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu. Należy pamiętać, że pliku Setup.bat używa narzędzia FindPrivateKey.exe, które jest zainstalowany, uruchamiając setupCertTool.bat z [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Uruchom aplikację klienta z \MetadataResolverClient\bin lub \SvcutilClient\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
3.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Usuń certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką. Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.  
  
#### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na komputerach  
  
1.  Na serwerze, uruchom `setup.bat service`. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z nazwą domeny pełni kwalifikowanymi maszyny i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
2.  Na serwerze należy edytować plik Web.config, aby odzwierciedlić nową nazwę certyfikatu. Oznacza to, zmień `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu, aby w pełni kwalifikowaną nazwą domeny maszyny.  
  
3.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
4.  Na komputerze klienckim, uruchom `setup.bat client`. Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie Client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.  
  
5.  W pliku App.config `MetadataResolverClient` na komputerze klienckim, zmień wartość adresu punktu końcowego mex odpowiadające nowy adres z usługą. Aby to zrobić, zastępując localhost w pełni kwalifikowaną nazwą domeny serwera. Wystąpienie "localhost" w pliku metadataResolverClient.cs należy również zmienić na nową nazwę certyfikatu usługi (nazwa domeny pełni kwalifikowanymi serwera). Tak samo postąpić w pliku App.config projektu SvcutilClient.  
  
6.  Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
7.  Na komputerze klienckim, uruchom `ImportServiceCert.bat`. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
8.  Na serwerze, uruchom `ImportClientCert.bat`, certyfikat klienta zostaną zaimportowane z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
9. Na komputerze usługi kompilacji projektu usługi w programie Visual Studio i wybierz stronę pomocy w przeglądarce sieci web, aby sprawdzić, czy jest uruchomiona.  
  
10. Na komputerze klienckim należy uruchomić MetadataResolverClient lub SvcutilClient z wersji programu VS.  
  
    1.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Zobacz też
