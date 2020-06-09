---
title: 'Instrukcje: określanie poświadczeń zabezpieczeń kanału'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 45a13460ce94cbacae0465fede4b455a2833ce81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596945"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="91ed1-102">Instrukcje: określanie poświadczeń zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="91ed1-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="91ed1-103">Moniker usługi Windows Communication Foundation (WCF) umożliwia aplikacjom COM wywoływanie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="91ed1-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="91ed1-104">Większość usług WCF wymaga od klienta określenia poświadczeń uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="91ed1-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="91ed1-105">Podczas wywoływania usługi WCF z poziomu klienta WCF można określić te poświadczenia w kodzie zarządzanym lub w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91ed1-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="91ed1-106">Podczas wywoływania usługi WCF z poziomu aplikacji modelu COM można użyć <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu, aby określić poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="91ed1-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="91ed1-107">W tym temacie przedstawiono różne sposoby określania poświadczeń przy użyciu <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="91ed1-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91ed1-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials>jest interfejsem IDispatch i nie uzyskasz funkcji IntelliSense w środowisku programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91ed1-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="91ed1-109">W tym artykule zostanie użyta usługa WCF zdefiniowana w [przykładzie zabezpieczenia wiadomości](../samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="91ed1-109">This article will use the WCF service defined in the [Message Security Sample](../samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="91ed1-110">Aby określić certyfikat klienta</span><span class="sxs-lookup"><span data-stu-id="91ed1-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="91ed1-111">Uruchom plik Setup. bat w katalogu zabezpieczeń wiadomości, aby utworzyć i zainstalować wymagane certyfikaty testowe.</span><span class="sxs-lookup"><span data-stu-id="91ed1-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="91ed1-112">Otwórz projekt zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="91ed1-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="91ed1-113">Dodaj `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` do `ICalculator` definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="91ed1-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="91ed1-114">Dodaj `bindingNamespace="http://Microsoft.ServiceModel.Samples"` do znacznika punktu końcowego w pliku App. config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="91ed1-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="91ed1-115">Utwórz próbkę zabezpieczenia komunikatów i uruchom Service. exe.</span><span class="sxs-lookup"><span data-stu-id="91ed1-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="91ed1-116">Użyj programu Internet Explorer i przejdź do identyfikatora URI usługi ( `http://localhost:8000/ServiceModelSamples/Service` ), aby upewnić się, że usługa działa.</span><span class="sxs-lookup"><span data-stu-id="91ed1-116">Use Internet Explorer and browse to the service's URI (`http://localhost:8000/ServiceModelSamples/Service`) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="91ed1-117">Otwórz Visual Basic 6,0 i Utwórz nowy plik w standardowym pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="91ed1-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="91ed1-118">Dodaj przycisk do formularza i kliknij dwukrotnie przycisk, aby dodać następujący kod do procedury obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="91ed1-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7. <span data-ttu-id="91ed1-119">Uruchom aplikację Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="91ed1-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="91ed1-120">Aplikacja Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodawanie (3, 4).</span><span class="sxs-lookup"><span data-stu-id="91ed1-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="91ed1-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>lub <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> można również użyć zamiast tego <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> , aby ustawić certyfikat klienta:</span><span class="sxs-lookup"><span data-stu-id="91ed1-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="91ed1-122">Aby to wywołanie działało, certyfikat klienta musi być zaufany na komputerze, na którym jest uruchomiony klient programu.</span><span class="sxs-lookup"><span data-stu-id="91ed1-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91ed1-123">Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci komunikat o błędzie informujący o nieprawidłowej składni.</span><span class="sxs-lookup"><span data-stu-id="91ed1-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="91ed1-124">Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="91ed1-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="91ed1-125">Aby określić nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="91ed1-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="91ed1-126">Zmodyfikuj plik App. config usługi, aby użyć programu `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="91ed1-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="91ed1-127">Jest to wymagane do weryfikacji nazwy użytkownika i hasła:</span><span class="sxs-lookup"><span data-stu-id="91ed1-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="91ed1-128">Ustaw `clientCredentialType` nazwę użytkownika na:</span><span class="sxs-lookup"><span data-stu-id="91ed1-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="91ed1-129">Otwórz Visual Basic 6,0 i Utwórz nowy plik w standardowym pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="91ed1-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="91ed1-130">Dodaj przycisk do formularza i kliknij dwukrotnie przycisk, aby dodać następujący kod do procedury obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="91ed1-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. <span data-ttu-id="91ed1-131">Uruchom aplikację Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="91ed1-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="91ed1-132">Aplikacja Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodawanie (3, 4).</span><span class="sxs-lookup"><span data-stu-id="91ed1-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91ed1-133">Powiązanie określone w monikerze usługi w tym przykładzie zostało zmienione na WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="91ed1-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="91ed1-134">Należy również pamiętać, że w wywołaniu metody należy podać prawidłową nazwę użytkownika i hasło <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="91ed1-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="91ed1-135">Aby określić poświadczenia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="91ed1-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="91ed1-136">Ustaw `clientCredentialType` dla systemu Windows w pliku App. config usługi:</span><span class="sxs-lookup"><span data-stu-id="91ed1-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="91ed1-137">Otwórz Visual Basic 6,0 i Utwórz nowy plik w standardowym pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="91ed1-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="91ed1-138">Dodaj przycisk do formularza i kliknij dwukrotnie przycisk, aby dodać następujący kod do procedury obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="91ed1-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="91ed1-139">Uruchom aplikację Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="91ed1-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="91ed1-140">Aplikacja Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodawanie (3, 4).</span><span class="sxs-lookup"><span data-stu-id="91ed1-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91ed1-141">Należy zastąpić wartości "Domain", "userID" i "Password" prawidłowymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="91ed1-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="91ed1-142">Aby określić token problemu</span><span class="sxs-lookup"><span data-stu-id="91ed1-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="91ed1-143">Tokeny wystawiania są używane tylko w przypadku aplikacji korzystających z zabezpieczeń federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="91ed1-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="91ed1-144">Aby uzyskać więcej informacji na temat zabezpieczeń federacyjnych, zobacz [federacyjne i wystawione tokeny](federation-and-issued-tokens.md) i [przykład Federacji](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="91ed1-144">For more information about federated security, see [Federation and Issued Tokens](federation-and-issued-tokens.md) and [Federation Sample](../samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="91ed1-145">Poniższy przykład kodu Visual Basic ilustruje sposób wywołania <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:</span><span class="sxs-lookup"><span data-stu-id="91ed1-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="91ed1-146">Aby uzyskać więcej informacji na temat parametrów dla tej metody, zobacz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="91ed1-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ed1-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91ed1-147">See also</span></span>

- [<span data-ttu-id="91ed1-148">Federacja</span><span class="sxs-lookup"><span data-stu-id="91ed1-148">Federation</span></span>](federation.md)
- [<span data-ttu-id="91ed1-149">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="91ed1-149">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="91ed1-150">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="91ed1-150">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="91ed1-151">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="91ed1-151">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="91ed1-152">Wiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="91ed1-152">Bindings and Security</span></span>](bindings-and-security.md)
