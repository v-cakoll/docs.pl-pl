---
title: Programowanie zabezpieczeń WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 1e82fbb266d3789a8d34109c66d9ee1d8a93c70c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463819"
---
# <a name="programming-wcf-security"></a>Programowanie zabezpieczeń WCF
W tym temacie opisano podstawowe zadania programowania używane do tworzenia bezpiecznej aplikacji Windows Communication Foundation (WCF). W tym temacie omówiono tylko uwierzytelnianie, poufność i integralność, zwane łącznie *zabezpieczeniami transferu.* Ten temat nie obejmuje autoryzacji (kontrola dostępu do zasobów lub usług); aby uzyskać informacje na temat autoryzacji, zobacz [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
> Aby uzyskać cenne wprowadzenie do koncepcji zabezpieczeń, zwłaszcza w odniesieniu do WCF, zobacz zestaw wzorców i praktyk samouczków na temat MSDN w [scenariuszach, wzorce i wskazówki dotyczące wdrażania dla ulepszeń usług sieci Web (GPW) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).  
  
 Programowanie zabezpieczeń WCF opiera się na trzech krokach, ustawienie następujące: tryb zabezpieczeń, typ poświadczeń klienta i wartości poświadczeń. Te kroki można wykonać za pomocą kodu lub konfiguracji.  
  
## <a name="setting-the-security-mode"></a>Ustawianie trybu zabezpieczeń  
 Poniżej wyjaśniono ogólne kroki programowania w trybie zabezpieczeń w WCF:  
  
1. Wybierz jeden ze wstępnie zdefiniowanych powiązań odpowiednich do wymagań aplikacji. Aby uzyskać listę opcji wiązania, zobacz [Powiązania dostarczone przez system](../../../../docs/framework/wcf/system-provided-bindings.md). Domyślnie prawie każde powiązanie ma włączone zabezpieczenia. Jedynym wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding> klasa (przy użyciu konfiguracji, [ \<podstawowehttpbinowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Wybrane powiązanie określa transport. Na przykład <xref:System.ServiceModel.WSHttpBinding> używa HTTP jako transportu; <xref:System.ServiceModel.NetTcpBinding> używa protokołu TCP.  
  
2. Wybierz jeden z trybów zabezpieczeń dla powiązania. Należy zauważyć, że wybrane powiązanie określa dostępne opcje trybu. Na przykład <xref:System.ServiceModel.WSDualHttpBinding> nie zezwala na bezpieczeństwo transportu (nie jest to opcja). Podobnie ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> zabezpieczenia wiadomości, <xref:System.ServiceModel.NetNamedPipeBinding> ani zezwala na to.  
  
     Masz trzy opcje:  
  
    1. `Transport`  
  
         Zabezpieczenia transportu zależy od mechanizmu, który został wybrany używa. Na przykład, jeśli `WSHttpBinding` używasz, to mechanizm zabezpieczeń jest Secure Sockets Layer (SSL) (również mechanizm dla protokołu HTTPS). Ogólnie rzecz biorąc, główną zaletą zabezpieczeń transportu jest to, że zapewnia dobrą przepustowość bez względu na to, którego transportu używasz. Jednak ma dwa ograniczenia: Po pierwsze jest to, że mechanizm transportu dyktuje typ poświadczeń używany do uwierzytelniania użytkownika. Jest to wadą tylko wtedy, gdy usługa musi współpracować z innymi usługami, które wymagają różnych typów poświadczeń. Po drugie, ponieważ zabezpieczenia nie są stosowane na poziomie wiadomości, zabezpieczenia są implementowane w sposób przeskoku, a nie end-to-end. To ostatnie ograniczenie jest problemem tylko wtedy, gdy ścieżka wiadomości między klientem a usługą zawiera pośredników. Aby uzyskać więcej informacji o tym, który transport ma być używany, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aby uzyskać więcej informacji na temat korzystania z zabezpieczeń transportu, zobacz [Omówienie zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2. `Message`  
  
         Zabezpieczenia wiadomości oznacza, że każda wiadomość zawiera niezbędne nagłówki i dane, aby zachować wiadomość bezpieczne. Ponieważ skład nagłówków jest różny, można dołączyć dowolną liczbę poświadczeń. Staje się to czynnikiem, jeśli są współdziałające z innymi usługami, które wymagają określonego typu poświadczeń, że mechanizm transportu nie może dostarczyć lub jeśli komunikat musi być używany z więcej niż jedną usługą, gdzie każda usługa wymaga innego typu poświadczeń.  
  
         Aby uzyskać więcej informacji, zobacz [Zabezpieczenia wiadomości](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Ten wybór używa warstwy transportu do zabezpieczenia transferu wiadomości, podczas gdy każda wiadomość zawiera poświadczenia bogate inne usługi potrzebują. Łączy to zaletę wydajności zabezpieczeń transportu z zaletą ekscesów bogatych zabezpieczeń wiadomości. Jest to dostępne z następującymi <xref:System.ServiceModel.WSFederationHttpBinding> <xref:System.ServiceModel.NetPeerTcpBinding>wiązaniami: <xref:System.ServiceModel.BasicHttpBinding>, , , i <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Jeśli zdecydujesz się użyć zabezpieczeń transportu dla protokołu HTTP (innymi słowy HTTPS), musisz również skonfigurować hosta z certyfikatem SSL i włączyć protokół SSL na porcie. Aby uzyskać więcej informacji, zobacz [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. Jeśli używasz <xref:System.ServiceModel.WSHttpBinding> i nie trzeba ustanawiać bezpiecznej <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> sesji, `false`ustaw właściwość na .  
  
     Bezpieczna sesja występuje, gdy klient i usługa utworzyć kanał przy użyciu klucza symetrycznego (zarówno klient, jak i serwer używają tego samego klucza dla długości konwersacji, dopóki okno dialogowe nie zostanie zamknięte).  
  
## <a name="setting-the-client-credential-type"></a>Ustawianie typu poświadczeń klienta  
 Wybierz odpowiedni typ poświadczeń klienta. Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Dostępne są następujące typy poświadczeń klienta:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 W zależności od sposobu ustawiania trybu należy ustawić typ poświadczeń. Na `wsHttpBinding`przykład, jeśli wybrano opcję , i ustawiono tryb na `clientCredentialType` "Wiadomość", można również ustawić atrybut `None`elementu `Windows` `UserName`Message `Certificate`na jedną z następujących wartości: , , , i `IssuedToken`, jak pokazano w poniższym przykładzie konfiguracji.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 Lub w kodzie:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Ustawianie wartości poświadczeń usługi  
 Po wybraniu typu poświadczeń klienta należy ustawić rzeczywiste poświadczenia dla usługi i klienta do użycia. W usłudze poświadczenia są ustawiane przy <xref:System.ServiceModel.Description.ServiceCredentials> użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> klasy <xref:System.ServiceModel.ServiceHostBase> i zwracane przez właściwość klasy. Powiązanie w użyciu implikuje typ poświadczeń usługi, wybrany tryb zabezpieczeń i typ poświadczeń klienta. Poniższy kod ustawia certyfikat dla poświadczeń usługi.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Ustawianie wartości poświadczeń klienta  
 Na kliencie ustaw wartości poświadczeń klienta przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy i zwrócone <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> przez właściwość <xref:System.ServiceModel.ClientBase%601> klasy. Poniższy kod ustawia certyfikat jako poświadczenie na kliencie przy użyciu protokołu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
