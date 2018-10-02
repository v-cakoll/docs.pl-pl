---
title: Dostawca tokenów
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
author: BrucePerlerMS
ms.openlocfilehash: b7b7750b51450d3b5d31b8034a20317ba03c49a4
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030145"
---
# <a name="token-provider"></a><span data-ttu-id="5daac-102">Dostawca tokenów</span><span class="sxs-lookup"><span data-stu-id="5daac-102">Token Provider</span></span>
<span data-ttu-id="5daac-103">Ten przykład demonstruje sposób implementacji niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="5daac-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="5daac-104">Dostawca tokenu w Windows Communication Foundation (WCF) jest używany dla podanie poświadczeń w celu infrastruktura zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5daac-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="5daac-105">Dostawcy tokenu, który sprawdza ogólnie rzecz biorąc, element docelowy i problemy odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5daac-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="5daac-106">Usługi WCF jest dostarczany z domyślny dostawca tokenu Menedżera poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="5daac-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="5daac-107">Usługi WCF jest również dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="5daac-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="5daac-108">Niestandardowego dostawcy tokenów są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="5daac-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="5daac-109">Jeśli masz Magazyn poświadczeń, który te dostawcy tokenów nie może działać z.</span><span class="sxs-lookup"><span data-stu-id="5daac-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="5daac-110">Jeśli chcesz udostępnić własny niestandardowy mechanizm przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje, na kiedy struktura klienta WCF przy użyciu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="5daac-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="5daac-111">Jeśli tworzysz niestandardowy token.</span><span class="sxs-lookup"><span data-stu-id="5daac-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="5daac-112">Niniejszy przykład pokazuje sposób tworzenia niestandardowego dostawcę tokenów, który przekształca dane wejściowe od użytkownika w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="5daac-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>  
  
 <span data-ttu-id="5daac-113">Aby podsumować, w przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="5daac-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="5daac-114">Jak klienta można uwierzytelniać za pomocą pary nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="5daac-114">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="5daac-115">Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="5daac-115">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="5daac-116">Jak serwer może sprawdzać poprawność poświadczeń klienta przy użyciu hasła za pomocą niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> który weryfikuje, czy nazwa użytkownika i hasło są zgodne.</span><span class="sxs-lookup"><span data-stu-id="5daac-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>  
  
-   <span data-ttu-id="5daac-117">Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="5daac-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="5daac-118">Niniejszy przykład pokazuje również, jak tożsamości elementu wywołującego jest dostępny po zakończeniu procesu niestandardowe uwierzytelnianie przy użyciu tokenów.</span><span class="sxs-lookup"><span data-stu-id="5daac-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="5daac-119">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config.</span><span class="sxs-lookup"><span data-stu-id="5daac-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="5daac-120">Punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5daac-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5daac-121">Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding`, która używa zabezpieczenia wiadomości domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5daac-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="5daac-122">W tym przykładzie ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="5daac-123">Usługa konfiguruje również certyfikat usługi, używając zachowania serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="5daac-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="5daac-124">Zachowanie serviceCredentials umożliwia skonfigurowanie certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="5daac-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="5daac-125">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi, a także zapewnienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5daac-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="5daac-126">Następująca konfiguracja odwołuje się do certyfikatu localhost, instalowana podczas instalacji przykładowej zgodnie z opisem w poniższych instrukcjach instalacji.</span><span class="sxs-lookup"><span data-stu-id="5daac-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
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
  
 <span data-ttu-id="5daac-127">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia.</span><span class="sxs-lookup"><span data-stu-id="5daac-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="5daac-128">Klient powiązanie skonfigurowano odpowiednie `Mode` i komunikat `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="5daac-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="5daac-129">Poniższe kroki pokazują, jak tworzenie niestandardowego dostawcy tokenów i zintegrować ją z architekturą WCF zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="5daac-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>  
  
1.  <span data-ttu-id="5daac-130">Pisania niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="5daac-130">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="5daac-131">Przykład implementuje niestandardowego dostawcy tokenu, który uzyskuje nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="5daac-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="5daac-132">Hasło musi być tą nazwą użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5daac-132">The password must match this username.</span></span> <span data-ttu-id="5daac-133">Ten dostawca tokenów niestandardowych jest tylko w celach demonstracyjnych i nie jest zalecane w przypadku rzeczywistych wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="5daac-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>  
  
     <span data-ttu-id="5daac-134">Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenów <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody.</span><span class="sxs-lookup"><span data-stu-id="5daac-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="5daac-135">Ta metoda tworzy i zwraca nowy `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="5daac-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="5daac-136">Napisz Menedżer tokenów zabezpieczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5daac-136">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="5daac-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla konkretnego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="5daac-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="5daac-138">Menedżer tokenów zabezpieczeń jest również używany do tworzenia wystawcy uwierzytelnienia tokenu i Serializator tokenów, ale te nie są objęte tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="5daac-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="5daac-139">W tym przykładzie Menedżer tokenów zabezpieczeń niestandardowe dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądana jest metoda do zwrócenia username niestandardowego dostawcy tokenów, jeśli przekazany wymagania tokenu wskazywać tego dostawcy nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5daac-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>  
  
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
  
3.  <span data-ttu-id="5daac-140">Wpisz poświadczenia niestandardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-140">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="5daac-141">Klasa poświadczeń klienta jest używany do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy zabezpieczeń Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatora.</span><span class="sxs-lookup"><span data-stu-id="5daac-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>  
  
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
  
4.  <span data-ttu-id="5daac-142">Konfigurowanie klienta do używania poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-142">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="5daac-143">Aby klientowi korzystanie z poświadczeń klienta niestandardowych przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
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
  
 <span data-ttu-id="5daac-144">W usłudze, aby wyświetlić informacje o wywołującym, użyj <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5daac-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="5daac-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera oświadczenia informacje dotyczące bieżącego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5daac-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 <span data-ttu-id="5daac-146">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5daac-147">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-147">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="5daac-148">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="5daac-148">Setup Batch File</span></span>  
 <span data-ttu-id="5daac-149">Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera z odpowiedni certyfikat, aby uruchomić samodzielnie hostowanej aplikacji, która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="5daac-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="5daac-150">Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="5daac-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="5daac-151">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="5daac-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="5daac-152">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="5daac-152">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="5daac-153">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5daac-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="5daac-154">`%SERVER_NAME%` Zmienna Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="5daac-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="5daac-155">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="5daac-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="5daac-156">Wartość domyślna, w tym pliku wsadowego to localhost.</span><span class="sxs-lookup"><span data-stu-id="5daac-156">The default value in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="5daac-157">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="5daac-157">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="5daac-158">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="5daac-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5daac-159">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5daac-160">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5daac-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="5daac-161">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wierszem polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="5daac-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="5daac-162">Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="5daac-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5daac-163">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="5daac-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="5daac-164">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="5daac-164">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="5daac-165">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5daac-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5daac-166">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5daac-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5daac-167">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="5daac-167">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="5daac-168">Uruchom Setup.bat z folderu instalacji przykładowej wewnątrz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5daac-168">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="5daac-169">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="5daac-169">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5daac-170">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5daac-170">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="5daac-171">Ustawić zmiennej środowiskowej PATH, w ramach [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia wskazuje katalog, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest.</span><span class="sxs-lookup"><span data-stu-id="5daac-171">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="5daac-172">Uruchom service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="5daac-172">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="5daac-173">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="5daac-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="5daac-174">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-174">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="5daac-175">W wierszu polecenia nazwy użytkownika, wpisz nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5daac-175">At the username prompt, type a user name.</span></span>  
  
5.  <span data-ttu-id="5daac-176">Hasła w wierszu należy użyć tego samego ciągu, który został wpisany monit o nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5daac-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6.  <span data-ttu-id="5daac-177">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5daac-177">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5daac-178">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="5daac-178">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="5daac-179">Utwórz katalog na komputerze usługi, aby pliki binarne usługi.</span><span class="sxs-lookup"><span data-stu-id="5daac-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="5daac-180">Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5daac-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="5daac-181">Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5daac-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="5daac-182">Musi mieć certyfikat serwera o nazwie podmiotu, który zawiera w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="5daac-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="5daac-183">Plik Service.exe.config należy zaktualizować w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5daac-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="5daac-184">Można utworzyć certyfikatu serwera, modyfikując plik wsadowy Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="5daac-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="5daac-185">Należy pamiętać, że plik Setup.bat jest należy uruchomić z wiersza polecenia programu Visual Studio, otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5daac-185">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="5daac-186">Należy ustawić `%SERVER_NAME%` zmiennej do hosta w pełni kwalifikowaną nazwę komputera, który jest używany do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="5daac-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="5daac-187">Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="5daac-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="5daac-188">Nie trzeba to zrobić, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="5daac-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="5daac-189">W pliku Service.exe.config na komputerze usługi Zmień wartość z adresu podstawowego, aby określić nazwę komputera w pełni kwalifikowaną, zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="5daac-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="5daac-190">Na komputerze usługi service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5daac-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="5daac-191">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5daac-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="5daac-192">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="5daac-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="5daac-193">Na komputerze klienckim, należy uruchomić `Client.exe` z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5daac-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="5daac-194">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5daac-194">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5daac-195">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="5daac-195">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="5daac-196">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="5daac-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daac-197">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5daac-197">See Also</span></span>
