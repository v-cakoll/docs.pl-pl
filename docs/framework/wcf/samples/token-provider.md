---
title: Dostawca tokenów
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 57b353ba945377d9056f7726d96befbd5466ffa6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481305"
---
# <a name="token-provider"></a>Dostawca tokenów
Ten przykład demonstruje sposób implementacji niestandardowego dostawcy tokenów. Dostawca tokenu w Windows Communication Foundation (WCF) jest używany dla podanie poświadczeń w celu infrastruktura zabezpieczeń. Dostawcy tokenu, który sprawdza ogólnie rzecz biorąc, element docelowy i problemy odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć wiadomości. Usługi WCF jest dostarczany z domyślny dostawca tokenu Menedżera poświadczeń. Usługi WCF jest również dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu. Niestandardowego dostawcy tokenów są przydatne w następujących przypadkach:  
  
-   Jeśli masz Magazyn poświadczeń, który te dostawcy tokenów nie może działać z.  
  
-   Jeśli chcesz udostępnić własny niestandardowy mechanizm przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje, na kiedy struktura klienta WCF przy użyciu poświadczeń.  
  
-   Jeśli tworzysz niestandardowy token.  
  
 Niniejszy przykład pokazuje sposób tworzenia niestandardowego dostawcę tokenów, który przekształca dane wejściowe od użytkownika w innym formacie.  
  
 Aby podsumować, w przykładzie pokazano poniżej:  
  
-   Jak klienta można uwierzytelniać za pomocą pary nazwy użytkownika i hasła.  
  
-   Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.  
  
-   Jak serwer może sprawdzać poprawność poświadczeń klienta przy użyciu hasła za pomocą niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> który weryfikuje, czy nazwa użytkownika i hasło są zgodne.  
  
-   Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 serwera.  
  
 Niniejszy przykład pokazuje również, jak tożsamości elementu wywołującego jest dostępny po zakończeniu procesu niestandardowe uwierzytelnianie przy użyciu tokenów.  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding`, która używa zabezpieczenia wiadomości domyślnie. W tym przykładzie ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika klienta. Usługa konfiguruje również certyfikat usługi, używając zachowania serviceCredentials. Zachowanie serviceCredentials umożliwia skonfigurowanie certyfikatu usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi, a także zapewnienia ochrony wiadomości. Następująca konfiguracja odwołuje się do certyfikatu localhost, instalowana podczas instalacji przykładowej zgodnie z opisem w poniższych instrukcjach instalacji.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia. Klient powiązanie skonfigurowano odpowiednie `Mode` i komunikat `clientCredentialType`.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="http://localhost:8000/servicemodelsamples/service"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator">  
    </endpoint>  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Poniższe kroki pokazują, jak tworzenie niestandardowego dostawcy tokenów i zintegrować ją z architekturą WCF zabezpieczeń:  
  
1.  Pisania niestandardowego dostawcy tokenów.  
  
     Przykład implementuje niestandardowego dostawcy tokenu, który uzyskuje nazwę użytkownika i hasło. Hasło musi być tą nazwą użytkownika. Ten dostawca tokenów niestandardowych jest tylko w celach demonstracyjnych i nie jest zalecane w przypadku rzeczywistych wdrożenia.  
  
     Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenów <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody. Ta metoda tworzy i zwraca nowy `UserNameSecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
        // obtain username and password from the user using console window  
        string username = GetUserName();  
        string password = GetPassword();  
        Console.WriteLine("username: {0}", username);  
  
        // return new UserNameSecurityToken containing information obtained from user  
        return new UserNameSecurityToken(username, password);  
    }  
    ```  
  
2.  Napisz Menedżer tokenów zabezpieczeń niestandardowych.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla konkretnego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody. Menedżer tokenów zabezpieczeń jest również używany do tworzenia wystawcy uwierzytelnienia tokenu i Serializator tokenów, ale te nie są objęte tego przykładu. W tym przykładzie Menedżer tokenów zabezpieczeń niestandardowe dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądana jest metoda do zwrócenia username niestandardowego dostawcy tokenów, jeśli przekazany wymagania tokenu wskazywać tego dostawcy nazwy użytkownika.  
  
    ```  
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        MyUserNameClientCredentials myUserNameClientCredentials;  
  
        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)  
            : base(myUserNameClientCredentials)  
        {  
            this.myUserNameClientCredentials = myUserNameClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // if token requirement matches username token return custom username token provider  
            // otherwise use base implementation  
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)  
            {  
                return new MyUserNameTokenProvider();  
            }  
            else  
            {  
                return base.CreateSecurityTokenProvider(tokenRequirement);  
            }  
        }  
    }  
    ```  
  
3.  Wpisz poświadczenia niestandardowego klienta.  
  
     Klasa poświadczeń klienta jest używany do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy zabezpieczeń Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatora.  
  
    ```  
    public class MyUserNameClientCredentials : ClientCredentials  
    {  
        public MyUserNameClientCredentials()  
            : base()  
        {  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new MyUserNameClientCredentials();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            // return custom security token manager  
            return new MyUserNameSecurityTokenManager(this);  
        }  
    }  
    ```  
  
4.  Konfigurowanie klienta do używania poświadczeń klienta.  
  
     Aby klientowi korzystanie z poświadczeń klienta niestandardowych przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.  
  
    ```  
    static void Main()  
    {  
        // ...  
           // Create a client with given client endpoint configuration  
          CalculatorClient client = new CalculatorClient();  
  
          // set new credentials  
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());  
       // ...  
    }  
    ```  
  
 W usłudze, aby wyświetlić informacje o wywołującym, użyj <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym przykładzie kodu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera oświadczenia informacje dotyczące bieżącego obiektu wywołującego.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera z odpowiedni certyfikat, aby uruchomić samodzielnie hostowanej aplikacji, która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.  
  
 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%` Zmienna Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Wartość domyślna, w tym pliku wsadowego to localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:  
  
     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wierszem polecenia Windows SDK. Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia Windows SDK.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom Setup.bat z folderu instalacji przykładowej wewnątrz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia otwartych z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Ustawić zmiennej środowiskowej PATH, w ramach [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia wskazuje katalog, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest.  
  
2.  Uruchom service.exe z service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  W wierszu polecenia nazwy użytkownika, wpisz nazwę użytkownika.  
  
5.  Hasła w wierszu należy użyć tego samego ciągu, który został wpisany monit o nazwę użytkownika.  
  
6.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi, aby pliki binarne usługi.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera o nazwie podmiotu, który zawiera w pełni kwalifikowana nazwa domeny komputera. Plik Service.exe.config należy zaktualizować w celu odzwierciedlenia tej nowej nazwy certyfikatu. Można utworzyć certyfikatu serwera, modyfikując plik wsadowy Setup.bat. Należy pamiętać, że plik Setup.bat jest należy uruchomić z wiersza polecenia programu Visual Studio, otwartych z uprawnieniami administratora. Należy ustawić `%SERVER_NAME%` zmiennej do hosta w pełni kwalifikowaną nazwę komputera, który jest używany do obsługi usługi.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta. Nie trzeba to zrobić, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.  
  
5.  W pliku Service.exe.config na komputerze usługi Zmień wartość z adresu podstawowego, aby określić nazwę komputera w pełni kwalifikowaną, zamiast nazwy localhost.  
  
6.  Na komputerze usługi service.exe należy uruchomić z wiersza polecenia.  
  
7.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim, należy uruchomić `Client.exe` z okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
## <a name="see-also"></a>Zobacz też
