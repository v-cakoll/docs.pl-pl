---
title: 'Instrukcje: określanie poświadczeń zabezpieczeń kanału'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 0bfbb71ade3822b9f504c2f89a41145ce0d435f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297983"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="df0d6-102">Instrukcje: określanie poświadczeń zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="df0d6-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="df0d6-103">Monikera programu Windows Communication Foundation (WCF) umożliwia aplikacji modelu COM do wywołania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="df0d6-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="df0d6-104">Większość usług WCF wymaga klienta określić poświadczenia dla uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="df0d6-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="df0d6-105">Podczas wywoływania usługi WCF z klienta programu WCF, te poświadczenia można określić w kodzie zarządzanym lub w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df0d6-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="df0d6-106">Podczas wywoływania usługi WCF z poziomu aplikacji modelu COM, można użyć <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu, aby określić poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="df0d6-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="df0d6-107">W tym temacie przedstawiają różne sposoby, aby określić poświadczenia, za pomocą <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="df0d6-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df0d6-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> jest interfejs IDispatch i nie będzie można uzyskać funkcji IntelliSense w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df0d6-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="df0d6-109">Ten artykuł będzie używana usługa WCF zdefiniowane w [zabezpieczenia komunikatów — przykład](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df0d6-109">This article will use the WCF service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="df0d6-110">Aby określić certyfikat klienta</span><span class="sxs-lookup"><span data-stu-id="df0d6-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="df0d6-111">Uruchom plik Setup.bat jest w katalogu zabezpieczeń wiadomości, tworzenie i instalowanie certyfikatów wymaganych testów.</span><span class="sxs-lookup"><span data-stu-id="df0d6-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="df0d6-112">Otwórz projekt zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="df0d6-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="df0d6-113">Dodaj `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` do `ICalculator` definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="df0d6-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="df0d6-114">Dodaj `bindingNamespace="http://Microsoft.ServiceModel.Samples"` do znacznika punktu końcowego w pliku App.config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="df0d6-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="df0d6-115">Zabezpieczenia komunikatów — przykład tworzenia i uruchom Service.exe.</span><span class="sxs-lookup"><span data-stu-id="df0d6-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="df0d6-116">W programie Internet Explorer i przejdź do identyfikatora URI usługi (http://localhost:8000/ServiceModelSamples/Service) aby upewnić się, że usługa działa.</span><span class="sxs-lookup"><span data-stu-id="df0d6-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="df0d6-117">Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych.</span><span class="sxs-lookup"><span data-stu-id="df0d6-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="df0d6-118">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="df0d6-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
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
  
7. <span data-ttu-id="df0d6-119">Uruchamianie aplikacji języka Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="df0d6-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="df0d6-120">Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodaj (3, 4).</span><span class="sxs-lookup"><span data-stu-id="df0d6-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="df0d6-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> lub <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> może również służyć zamiast <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> można ustawić certyfikatu klienta:</span><span class="sxs-lookup"><span data-stu-id="df0d6-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="df0d6-122">Dla tego wywołania do pracy, musi być uważany za zaufany na maszynie którą klient jest uruchomiony na certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="df0d6-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df0d6-123">Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o "Nieprawidłową składnię."</span><span class="sxs-lookup"><span data-stu-id="df0d6-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="df0d6-124">Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="df0d6-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="df0d6-125">Aby określić nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="df0d6-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="df0d6-126">Zmodyfikuj plik App.config usługi, aby użyć `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="df0d6-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="df0d6-127">Jest to wymagane do weryfikacji nazwy i hasła użytkownika:</span><span class="sxs-lookup"><span data-stu-id="df0d6-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="df0d6-128">Ustaw `clientCredentialType` na nazwę użytkownika:</span><span class="sxs-lookup"><span data-stu-id="df0d6-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="df0d6-129">Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych.</span><span class="sxs-lookup"><span data-stu-id="df0d6-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="df0d6-130">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="df0d6-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. <span data-ttu-id="df0d6-131">Uruchamianie aplikacji języka Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="df0d6-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="df0d6-132">Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodaj (3, 4).</span><span class="sxs-lookup"><span data-stu-id="df0d6-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df0d6-133">Powiązanie określone w monikera w tym przykładzie został zmieniony na WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="df0d6-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="df0d6-134">Należy również zauważyć, że należy podać prawidłową nazwę użytkownika i hasło w wywołaniu <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="df0d6-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="df0d6-135">Aby określić poświadczenia Windows</span><span class="sxs-lookup"><span data-stu-id="df0d6-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="df0d6-136">Ustaw `clientCredentialType` do Windows w pliku App.config usługi:</span><span class="sxs-lookup"><span data-stu-id="df0d6-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="df0d6-137">Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych.</span><span class="sxs-lookup"><span data-stu-id="df0d6-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="df0d6-138">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="df0d6-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="df0d6-139">Uruchamianie aplikacji języka Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="df0d6-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="df0d6-140">Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodaj (3, 4).</span><span class="sxs-lookup"><span data-stu-id="df0d6-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df0d6-141">Prawidłowymi wartościami, musisz zastąpić "domenę", "userID" i "password".</span><span class="sxs-lookup"><span data-stu-id="df0d6-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="df0d6-142">Aby określić token problem</span><span class="sxs-lookup"><span data-stu-id="df0d6-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="df0d6-143">Tokeny problemu są używane tylko w przypadku aplikacji korzystających z federacyjnego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="df0d6-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="df0d6-144">Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) i [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df0d6-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="df0d6-145">Poniższy przykład kodu w języku Visual Basic ilustruje sposób wywołania metody <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:</span><span class="sxs-lookup"><span data-stu-id="df0d6-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="df0d6-146">Aby uzyskać więcej informacji na temat parametrów dla tej metody, zobacz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="df0d6-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df0d6-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df0d6-147">See also</span></span>

- [<span data-ttu-id="df0d6-148">Federacja</span><span class="sxs-lookup"><span data-stu-id="df0d6-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)
- [<span data-ttu-id="df0d6-149">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="df0d6-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="df0d6-150">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="df0d6-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="df0d6-151">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="df0d6-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="df0d6-152">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="df0d6-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
