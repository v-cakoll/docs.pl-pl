---
title: "Dostawca tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bd6b0983dcb4a0f7cdbabc5b391cca2000f9d16d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="token-provider"></a>Dostawca tokenów
W tym przykładzie pokazano, jak do zaimplementowania niestandardowego dostawcy tokenu. Dostawca tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do podawania poświadczeń w celu zabezpieczenia infrastruktury. Dostawca tokenu ogólnie sprawdza obiektu docelowego i problemów odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć komunikatu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jest dostarczany z domyślnym dostawcy tokenu Menedżera poświadczeń. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]również jest dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu. Tokenów niestandardowi są przydatne w następujących przypadkach:  
  
-   Jeśli masz Magazyn poświadczeń, które tych dostawców tokenu nie może pracować z.  
  
-   Jeśli chcesz udostępnić własny niestandardowy mechanizm do przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje o tym, kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta używa poświadczeń.  
  
-   Jeśli tworzysz niestandardowy token.  
  
 Ten przykład przedstawia sposób tworzenia niestandardowego dostawcę tokenów, który przekształca danych wejściowych od użytkownika w innym formacie.  
  
 Krótko mówiąc, w tym przykładzie przedstawiono poniżej:  
  
-   Jak klient może uwierzytelnić przy użyciu pary nazwy użytkownika i hasła.  
  
-   Jak można skonfigurować klienta z niestandardowego dostawcy tokenu.  
  
-   Jak serwer można sprawdzić poprawności poświadczeń klienta przy użyciu hasła z niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> która weryfikuje, że nazwa użytkownika i hasło są zgodne.  
  
-   Jak serwer jest uwierzytelniany przez klienta przy użyciu certyfikat X.509.  
  
 W tym przykładzie przedstawiono również sposób tożsamości obiektu wywołującego jest dostępny po zakończeniu uwierzytelniania tokenu niestandardowego.  
  
 Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z normą `wsHttpBinding`, która używa zabezpieczenia wiadomości domyślnie. W tym przykładzie ustawia standardowego `wsHttpBinding` uwierzytelniania nazwa użytkownika klienta. Usługa konfiguruje również certyfikat usługi, używając zachowania serviceCredentials. Zachowanie serviceCredentials umożliwia konfigurowanie certyfikatu usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewnienia ochrony wiadomości. Następująca konfiguracja odwołuje się do certyfikatu localhost zainstalowane podczas instalacji próbki zgodnie z opisem w poniższych instrukcjach instalacji.  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu. Klient powiązanie jest skonfigurowany z użyciem odpowiednich `Mode` i komunikat `clientCredentialType`.  
  
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
  
 Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenu i ich integracji z programem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] strukturę zabezpieczeń:  
  
1.  Pisanie niestandardowych dostawcy tokenu.  
  
     Przykład implementuje niestandardowego dostawcę tokenów, który uzyskuje nazwę użytkownika i hasło. Hasło musi być tą nazwą użytkownika. Ten dostawca tokenów niestandardowych jest tylko w celach demonstracyjnych i nie jest zalecane do pracy w rzeczywistych wdrożenia.  
  
     Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody. Ta metoda tworzy i zwraca nowy `UserNameSecurityToken`.  
  
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
  
2.  Zapis Menedżer tokenów zabezpieczających niestandardowych.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody. Menedżer tokenów zabezpieczających jest również używane do utworzenia wystawcy uwierzytelnienia tokenu i serializatora tokenu, ale te nie są objęte w tym przykładzie. W tym przykładzie Menedżer tokenów zabezpieczających niestandardowych dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądanej metody zwracane dostawcy tokenów niestandardowej nazwy użytkownika w przypadku tego dostawcy username wskazują przekazany wymagania tokenu.  
  
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
  
     Klasa poświadczeń klienta jest używana do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i Serializator tokenu zabezpieczeń.  
  
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
  
4.  Skonfigurować klienta do używania poświadczeń klienta.  
  
     Aby klientowi korzystanie z poświadczeń klienta niestandardowych próbka usuwa domyślną klasę poświadczeń klienta i udostępnia nową klasę poświadczeń klienta.  
  
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
  
 W usłudze, aby wyświetlić informacje o wywołującym, użyj <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym przykładzie kodu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera oświadczenia informacje o bieżącym wywołującego.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiedni certyfikat do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej przedstawiono krótkie omówienie różne sekcje pliki wsadowe, tak, aby można modyfikować w prawidłowej konfiguracji:  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. `%SERVER_NAME%` Zmiennej określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Wartość domyślna w tym pliku wsadowego to localhost.  
  
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
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia systemu Windows SDK. Wymaga ona, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia systemu Windows SDK.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom z folderu instalacji próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
2.  Uruchom service.exe z service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  W wierszu polecenia nazwy użytkownika wpisz nazwę użytkownika.  
  
5.  W wierszu hasła należy użyć te same parametry, które zostało wpisane monit o nazwę użytkownika.  
  
6.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi dla usługi danych binarnych.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera. Plik Service.exe.config trzeba zaktualizować do uwzględnienia tej nowej nazwy certyfikatu. Można utworzyć certyfikatu serwera, modyfikując plik wsadowy pliku Setup.bat. Należy pamiętać, że plik pliku setup.bat należy uruchomić z wiersza polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Należy ustawić `%SERVER_NAME%` zmiennych hosta w pełni kwalifikowaną nazwę komputera, na którym jest używany do obsługi usługi.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta. Nie trzeba w tym momencie wystawienia certyfikatu serwera przez klienta zaufanego wystawcy.  
  
5.  W pliku Service.exe.config na komputerze usługi Zmień wartość adres podstawowy, aby określić nazwę komputera w pełni kwalifikowaną zamiast localhost.  
  
6.  Na komputerze, usługi uruchom service.exe z wiersza polecenia.  
  
7.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.  
  
9. Na komputerze klienckim, otwórz `Client.exe` z poziomu okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
## <a name="see-also"></a>Zobacz też
