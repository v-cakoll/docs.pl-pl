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
# <a name="how-to-specify-channel-security-credentials"></a>Instrukcje: określanie poświadczeń zabezpieczeń kanału
Monikera programu Windows Communication Foundation (WCF) umożliwia aplikacji modelu COM do wywołania usługi WCF. Większość usług WCF wymaga klienta określić poświadczenia dla uwierzytelniania i autoryzacji. Podczas wywoływania usługi WCF z klienta programu WCF, te poświadczenia można określić w kodzie zarządzanym lub w pliku konfiguracji aplikacji. Podczas wywoływania usługi WCF z poziomu aplikacji modelu COM, można użyć <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu, aby określić poświadczenia. W tym temacie przedstawiają różne sposoby, aby określić poświadczenia, za pomocą <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interfejsu.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> jest interfejs IDispatch i nie będzie można uzyskać funkcji IntelliSense w środowisku Visual Studio.  
  
 Ten artykuł będzie używana usługa WCF zdefiniowane w [zabezpieczenia komunikatów — przykład](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Aby określić certyfikat klienta  
  
1. Uruchom plik Setup.bat jest w katalogu zabezpieczeń wiadomości, tworzenie i instalowanie certyfikatów wymaganych testów.  
  
2. Otwórz projekt zabezpieczenia wiadomości.  
  
3. Dodaj `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` do `ICalculator` definicji interfejsu.  
  
4. Dodaj `bindingNamespace="http://Microsoft.ServiceModel.Samples"` do znacznika punktu końcowego w pliku App.config dla usługi.  
  
5. Zabezpieczenia komunikatów — przykład tworzenia i uruchom Service.exe. W programie Internet Explorer i przejdź do identyfikatora URI usługi (http://localhost:8000/ServiceModelSamples/Service) aby upewnić się, że usługa działa.  
  
6. Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:  
  
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
  
7. Uruchamianie aplikacji języka Visual Basic i sprawdź wyniki.  
  
     Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodaj (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> lub <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> może również służyć zamiast <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> można ustawić certyfikatu klienta:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Dla tego wywołania do pracy, musi być uważany za zaufany na maszynie którą klient jest uruchomiony na certyfikat klienta.  
  
> [!NOTE]
>  Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o "Nieprawidłową składnię." Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.  
  
### <a name="to-specify-user-name-and-password"></a>Aby określić nazwę użytkownika i hasło  
  
1. Zmodyfikuj plik App.config usługi, aby użyć `wsHttpBinding`. Jest to wymagane do weryfikacji nazwy i hasła użytkownika:  

2. Ustaw `clientCredentialType` na nazwę użytkownika:  

3. Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:  
  
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
  
4. Uruchamianie aplikacji języka Visual Basic i sprawdź wyniki. Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodaj (3, 4).  
  
    > [!NOTE]
    >  Powiązanie określone w monikera w tym przykładzie został zmieniony na WSHttpBinding_ICalculator. Należy również zauważyć, że należy podać prawidłową nazwę użytkownika i hasło w wywołaniu <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>Aby określić poświadczenia Windows  
  
1. Ustaw `clientCredentialType` do Windows w pliku App.config usługi:  

2. Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:  
  
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
  
3. Uruchamianie aplikacji języka Visual Basic i sprawdź wyniki. Aplikacji Visual Basic wyświetli okno komunikatu z wynikiem wywołania Dodaj (3, 4).  
  
    > [!NOTE]
    >  Prawidłowymi wartościami, musisz zastąpić "domenę", "userID" i "password".  
  
### <a name="to-specify-an-issue-token"></a>Aby określić token problem  
  
1. Tokeny problemu są używane tylko w przypadku aplikacji korzystających z federacyjnego zabezpieczenia. Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) i [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     Poniższy przykład kodu w języku Visual Basic ilustruje sposób wywołania metody <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> metody:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Aby uzyskać więcej informacji na temat parametrów dla tej metody, zobacz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Zobacz także

- [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
