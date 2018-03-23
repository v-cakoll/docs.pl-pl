---
title: 'Porady: Określ poświadczenia zabezpieczeń kanału'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: ''
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: e2aedb06ec694f6c7dfb12b70ab919ae23eed17e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="8c939-102">Porady: Określ poświadczenia zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="8c939-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="8c939-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Moniker usługi umożliwia aplikacjom COM, wywołanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="8c939-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Service Moniker allows COM applications to call [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="8c939-104">Większość [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług wymaga od klienta określić poświadczenia dla uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="8c939-104">Most [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="8c939-105">Podczas wywoływania metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, można określić te poświadczenia w kodzie zarządzanym lub w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c939-105">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="8c939-106">Podczas wywoływania metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z aplikacji modelu COM, możesz użyć <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejs, aby określić poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="8c939-106">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="8c939-107">W tym temacie przedstawiają różne sposoby, aby określić poświadczenia, za pomocą <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8c939-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c939-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> jest interfejs IDispatch i nie otrzyma funkcja IntelliSense w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c939-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="8c939-109">W tym artykule będzie używać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zdefiniowany w [zabezpieczenia komunikatów — przykład](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8c939-109">This article will use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="8c939-110">Aby określić certyfikat klienta</span><span class="sxs-lookup"><span data-stu-id="8c939-110">To specify a client certificate</span></span>  
  
1.  <span data-ttu-id="8c939-111">Uruchom plik pliku Setup.bat w katalogu zabezpieczenia komunikatów do tworzenia i instalowania certyfikatów wymaganych testów.</span><span class="sxs-lookup"><span data-stu-id="8c939-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2.  <span data-ttu-id="8c939-112">Otwórz projekt zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8c939-112">Open the Message Security project.</span></span>  
  
3.  <span data-ttu-id="8c939-113">Dodaj `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` do `ICalculator` definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8c939-113">Add `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` to the `ICalculator` interface definition.</span></span>  
  
4.  <span data-ttu-id="8c939-114">Dodaj `bindingNamespace=``http://Microsoft.ServiceModel.Samples` do tagu końcowego w pliku App.config dla usługi.</span><span class="sxs-lookup"><span data-stu-id="8c939-114">Add `bindingNamespace=``http://Microsoft.ServiceModel.Samples` to the endpoint tag in the App.config for the service.</span></span>  
  
5.  <span data-ttu-id="8c939-115">Tworzenie przykładowej zabezpieczeń komunikatów i uruchamianie Service.exe.</span><span class="sxs-lookup"><span data-stu-id="8c939-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="8c939-116">W programie Internet Explorer i przejdź do identyfikatora URI usługi (Service-http://localhost: 8000/ServiceModelSamples) aby upewnić się, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="8c939-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6.  <span data-ttu-id="8c939-117">Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa.</span><span class="sxs-lookup"><span data-stu-id="8c939-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8c939-118">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="8c939-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
7.  <span data-ttu-id="8c939-119">Uruchamianie aplikacji Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="8c939-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="8c939-120">Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem z wywołaniem Dodaj (3, 4).</span><span class="sxs-lookup"><span data-stu-id="8c939-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="8c939-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> lub <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> można również zamiast <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> można ustawić certyfikatu klienta:</span><span class="sxs-lookup"><span data-stu-id="8c939-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="8c939-122">Dla tego wywołania do pracy certyfikat klienta musi być zaufany na komputerze, na którym działa klient na.</span><span class="sxs-lookup"><span data-stu-id="8c939-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c939-123">Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłową składnię."</span><span class="sxs-lookup"><span data-stu-id="8c939-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="8c939-124">Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="8c939-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="8c939-125">Aby określić nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="8c939-125">To specify user name and password</span></span>  
  
1.  <span data-ttu-id="8c939-126">Zmodyfikuj plik App.config usługi do użycia `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8c939-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="8c939-127">Jest to wymagane do weryfikacji nazwy i hasła użytkownika:</span><span class="sxs-lookup"><span data-stu-id="8c939-127">This is required for user name and password validation:</span></span>  
  
  
  
2.  <span data-ttu-id="8c939-128">Ustaw `clientCredentialType` na nazwę użytkownika:</span><span class="sxs-lookup"><span data-stu-id="8c939-128">Set the `clientCredentialType` to UserName:</span></span>  
  
  
  
3.  <span data-ttu-id="8c939-129">Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa.</span><span class="sxs-lookup"><span data-stu-id="8c939-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8c939-130">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="8c939-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
4.  <span data-ttu-id="8c939-131">Uruchamianie aplikacji Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="8c939-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="8c939-132">Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem z wywołaniem Dodaj (3, 4).</span><span class="sxs-lookup"><span data-stu-id="8c939-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c939-133">Powiązanie określonym w monikerze usługi, w tym przykładzie został zmieniony na WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="8c939-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="8c939-134">Należy również zauważyć, że należy podać prawidłową nazwę użytkownika i hasło w wywołaniu <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="8c939-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="8c939-135">Aby określić poświadczenia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8c939-135">To specify Windows Credentials</span></span>  
  
1.  <span data-ttu-id="8c939-136">Ustaw `clientCredentialType` do systemu Windows w pliku App.config usługi:</span><span class="sxs-lookup"><span data-stu-id="8c939-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  
  
  
  
2.  <span data-ttu-id="8c939-137">Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa.</span><span class="sxs-lookup"><span data-stu-id="8c939-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8c939-138">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="8c939-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
3.  <span data-ttu-id="8c939-139">Uruchamianie aplikacji Visual Basic i sprawdź wyniki.</span><span class="sxs-lookup"><span data-stu-id="8c939-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="8c939-140">Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem z wywołaniem Dodaj (3, 4).</span><span class="sxs-lookup"><span data-stu-id="8c939-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c939-141">"Domenę", "userID" i "password" należy zamienić na prawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="8c939-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="8c939-142">Aby określić token problem</span><span class="sxs-lookup"><span data-stu-id="8c939-142">To specify an issue token</span></span>  
  
1.  <span data-ttu-id="8c939-143">Problem tokeny są używane tylko do aplikacji przy użyciu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8c939-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="8c939-144">Aby uzyskać więcej informacji dotyczących zabezpieczeń, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) i [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8c939-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="8c939-145">Poniższy przykład kodu języka Visual Basic przedstawiono sposób wywoływania <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:</span><span class="sxs-lookup"><span data-stu-id="8c939-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="8c939-146">Aby uzyskać więcej informacji na temat parametrów dla tej metody, zobacz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="8c939-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c939-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c939-147">See Also</span></span>  
 [<span data-ttu-id="8c939-148">Federacja</span><span class="sxs-lookup"><span data-stu-id="8c939-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="8c939-149">Instrukcje: konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="8c939-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="8c939-150">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="8c939-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="8c939-151">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="8c939-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="8c939-152">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="8c939-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
