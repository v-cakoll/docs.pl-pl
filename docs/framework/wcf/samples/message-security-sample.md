---
title: Zabezpieczenia komunikatów — przykład
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 1e57e82dc9394f34ab97da751a5d11c6099d353c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044860"
---
# <a name="message-security-sample"></a>Zabezpieczenia komunikatów — przykład
Ten przykład pokazuje, jak zaimplementować aplikację, która korzysta z `basicHttpBinding` i zabezpieczenia komunikatów. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 `basicHttpBinding` Tryb zabezpieczeń można ustawić na następujące wartości: `TransportWithMessageCredential` `Message`, `Transport`, `TransportCredentialOnly` i `None`. W poniższym przykładowym pliku App Service. config definicja punktu końcowego określa `basicHttpBinding` i odwołuje się do konfiguracji powiązania o nazwie `Binding1`, jak pokazano w poniższej konfiguracji przykładowej:  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 Konfiguracja powiązania ustawia `mode` atrybut [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` zabezpieczeńnai`Certificate` ustawia [ atrybut>komunikatutak,jakpokazanowponiższymprzykładzie\<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) `clientCredentialType` . Przykładowa konfiguracja:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Certyfikat, którego używa Usługa do samodzielnego uwierzytelnienia klienta, jest ustawiany w sekcji zachowania w pliku konfiguracji w obszarze `serviceCredentials` elementu. Tryb walidacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia w usłudze, jest również ustawiany w sekcji zachowania `clientCertificate` w obszarze elementu.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 W pliku konfiguracji klienta określono te same informacje o powiązaniu i zabezpieczeniach.  
  
 Tożsamość obiektu wywołującego jest wyświetlana w oknie konsoli usługi przy użyciu następującego kodu:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Uruchom setup. bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.  
  
    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK. Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK.  
  
2. Uruchom aplikację usługi z \service\bin.  
  
3. Uruchom aplikację kliencką z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Usuń certyfikaty, uruchamiając Oczyść. bat po zakończeniu korzystania z przykładu. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na wielu maszynach  
  
1. Utwórz katalog na komputerze usługi dla plików binarnych usługi.  
  
2. Skopiuj pliki programu Service Files do katalogu usługi na serwerze programu. Skopiuj także pliki Setup. bat, Oczyść. bat i ImportClientCert. bat na serwer.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
5. Na serwerze uruchom `setup.bat service`polecenie. `setup.bat` Uruchomienie`service` z argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny maszyny i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
6. Edytuj plik Service. exe. config, aby odzwierciedlić nową nazwę certyfikatu ( `findValue` w atrybucie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) w elemencie serviceCertificate >), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera. Zmień również wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego`.`  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. Na kliencie Uruchom `setup.bat client`polecenie. `setup.bat` Uruchomienie`client` z argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.  
  
9. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Można to zrobić, zastępując localhost nazwą domeny, w której jest w pełni kwalifikowana. Zmień `findValue` również atrybut [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nową nazwę certyfikatu usługi, która jest w pełni kwalifikowaną nazwą domeny serwera.  
  
10. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.  
  
11. Na kliencie Uruchom program ImportServiceCert. bat. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
12. Na serwerze programu Uruchom program ImportClientCert. bat, który importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.  
  
13. Na maszynie usługi Uruchom program Service. exe z wiersza polecenia.  
  
14. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.  
  
    1. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między maszynami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między maszynami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
