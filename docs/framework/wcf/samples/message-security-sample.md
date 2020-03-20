---
title: Zabezpieczenia komunikatów — przykład
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183517"
---
# <a name="message-security-sample"></a>Zabezpieczenia komunikatów — przykład
W tym przykładzie pokazano, jak zaimplementować aplikację, która używa `basicHttpBinding` zabezpieczeń i wiadomości. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Tryb zabezpieczeń `basicHttpBinding` można ustawić na następujące `Message`wartości: `TransportWithMessageCredential` `TransportCredentialOnly` , `None` `Transport`, i . W poniższej przykładowej usłudze App.config plik, `basicHttpBinding` definicja punktu końcowego określa i odwołuje się do konfiguracji powiązania o nazwie `Binding1`, jak pokazano w następującej konfiguracji przykładowej:  
  
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
  
 Konfiguracja powiązania `mode` ustawia atrybut [ \<>zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` i ustawia `clientCredentialType` atrybut [ \<komunikatu>,](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) `Certificate` jak pokazano w poniższej przykładowej konfiguracji:  
  
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
  
 Certyfikat, który usługa używa do uwierzytelniania się do klienta jest ustawiona w `serviceCredentials` sekcji zachowania pliku konfiguracji w ramach elementu. Tryb sprawdzania poprawności, który ma zastosowanie do certyfikatu, który klient używa do uwierzytelniania się `clientCertificate` do usługi jest również ustawiony w sekcji zachowania w ramach elementu.  
  
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
  
 Te same szczegóły powiązania i zabezpieczeń są określone w pliku konfiguracji klienta.  
  
 Tożsamość wywołującego jest wyświetlana w oknie konsoli usługi przy użyciu następującego kodu:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i utworzyć próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Uruchom plik Setup.bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.  
  
    > [!NOTE]
    > Plik wsadowy setup.bat jest przeznaczony do uruchamiania z wiersza polecenia SDK systemu Windows. Wymaga to, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym jest zainstalowany pakiet SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia zestawu Windows SDK.  
  
2. Uruchom aplikację usługi z \service\bin.  
  
3. Uruchom aplikację kliencką z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Usuń certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Utwórz katalog na komputerze serwisowym dla plików binarnych usług.  
  
2. Skopiuj pliki programu serwisowego do katalogu usług na serwerze. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na serwer.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5. Na serwerze `setup.bat service`uruchom program . Uruchamianie `setup.bat` `service` z argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6. Edytuj service.exe.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element), który jest taki sam jak w pełni kwalifikowana nazwa domeny komputera. Zmień również wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego`.`  
  
7. Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. Na kliencie `setup.bat client`uruchom program . Uruchamianie `setup.bat` `client` z argumentem tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować nowy adres usługi. Można to zrobić, zastępując localhost w pełni kwalifikowaną nazwą domeny serwera. Zmień również `findValue` atrybut [ \<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nową nazwę certyfikatu usługi, która jest w pełni kwalifikowaną nazwą domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na kliencie uruchom plik ImportServiceCert.bat. Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.  
  
12. Na serwerze uruchom plik ImportClientCert.bat, Spowoduje to zaimportowanie certyfikatu klienta z pliku Client.cer do magazynu LocalMachine — TrustedPeople.  
  
13. Na komputerze serwisowym uruchom program Service.exe z wiersza polecenia.  
  
14. Na komputerze klienckim uruchom program Client.exe z okna wiersza polecenia.  
  
    1. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
    > [!NOTE]
    > Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli zostały uruchomione windows communication foundation (WCF) przykłady, które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w CurrentUser — TrustedPeople magazynu. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
