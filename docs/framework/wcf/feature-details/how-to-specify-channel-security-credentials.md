---
title: "Porady: Określ poświadczenia zabezpieczeń kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e2aedb06ec694f6c7dfb12b70ab919ae23eed17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-channel-security-credentials"></a>Porady: Określ poświadczenia zabezpieczeń kanału
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Moniker usługi umożliwia aplikacjom COM, wywołanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług. Większość [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług wymaga od klienta określić poświadczenia dla uwierzytelniania i autoryzacji. Podczas wywoływania metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, można określić te poświadczenia w kodzie zarządzanym lub w pliku konfiguracyjnym aplikacji. Podczas wywoływania metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z aplikacji modelu COM, możesz użyć <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejs, aby określić poświadczenia. W tym temacie przedstawiają różne sposoby, aby określić poświadczenia, za pomocą <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials>jest interfejs IDispatch i nie otrzyma funkcja IntelliSense w środowisku Visual Studio.  
  
 W tym artykule będzie używać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zdefiniowany w [zabezpieczenia komunikatów — przykład](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Aby określić certyfikat klienta  
  
1.  Uruchom plik pliku Setup.bat w katalogu zabezpieczenia komunikatów do tworzenia i instalowania certyfikatów wymaganych testów.  
  
2.  Otwórz projekt zabezpieczeń wiadomości.  
  
3.  Dodaj `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` do `ICalculator` definicji interfejsu.  
  
4.  Dodaj `bindingNamespace=``http://Microsoft.ServiceModel.Samples` do tagu końcowego w pliku App.config dla usługi.  
  
5.  Tworzenie przykładowej zabezpieczeń komunikatów i uruchamianie Service.exe. W programie Internet Explorer i przejdź do identyfikatora URI usługi (Service-http://localhost: 8000/ServiceModelSamples) aby upewnić się, że usługa jest uruchomiona.  
  
6.  Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:  
  
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
  
7.  Uruchamianie aplikacji Visual Basic i sprawdź wyniki.  
  
     Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem z wywołaniem Dodaj (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>lub <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> można również zamiast <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> można ustawić certyfikatu klienta:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Dla tego wywołania do pracy certyfikat klienta musi być zaufany na komputerze, na którym działa klient na.  
  
> [!NOTE]
>  Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłową składnię." Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.  
  
### <a name="to-specify-user-name-and-password"></a>Aby określić nazwę użytkownika i hasło  
  
1.  Zmodyfikuj plik App.config usługi do użycia `wsHttpBinding`. Jest to wymagane do weryfikacji nazwy i hasła użytkownika:  
  
  
  
2.  Ustaw `clientCredentialType` na nazwę użytkownika:  
  
  
  
3.  Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:  
  
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
  
4.  Uruchamianie aplikacji Visual Basic i sprawdź wyniki. Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem z wywołaniem Dodaj (3, 4).  
  
    > [!NOTE]
    >  Powiązanie określonym w monikerze usługi, w tym przykładzie został zmieniony na WSHttpBinding_ICalculator. Należy również zauważyć, że należy podać prawidłową nazwę użytkownika i hasło w wywołaniu <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>Aby określić poświadczenia systemu Windows  
  
1.  Ustaw `clientCredentialType` do systemu Windows w pliku App.config usługi:  
  
  
  
2.  Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:  
  
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
  
3.  Uruchamianie aplikacji Visual Basic i sprawdź wyniki. Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem z wywołaniem Dodaj (3, 4).  
  
    > [!NOTE]
    >  "Domenę", "userID" i "password" należy zamienić na prawidłowe wartości.  
  
### <a name="to-specify-an-issue-token"></a>Aby określić token problem  
  
1.  Problem tokeny są używane tylko do aplikacji przy użyciu zabezpieczeń. Aby uzyskać więcej informacji dotyczących zabezpieczeń, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) i [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Poniższy przykład kodu języka Visual Basic przedstawiono sposób wywoływania <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Aby uzyskać więcej informacji na temat parametrów dla tej metody, zobacz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Zobacz też  
 [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
