---
title: Programowanie zabezpieczeń WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 1cb18f1be8e418ace4c9f9f71b7f97ac37ff8074
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193893"
---
# <a name="programming-wcf-security"></a>Programowanie zabezpieczeń WCF
W tym temacie opisano podstawowe zadania programowania, służące do tworzenia bezpiecznych aplikacji Windows Communication Foundation (WCF). W tym temacie omówiono uwierzytelniania, poufności i integralności, nazywane zbiorczo *transferu zabezpieczeń*. W tym temacie nie omówiono autoryzacji (kontrola dostępu do zasobów lub usług); Aby uzyskać informacje dotyczące autoryzacji, zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Cenne wprowadzenie do pojęcia dotyczące zabezpieczeń, szczególnie w odniesieniu do usługi WCF, zobacz zestaw wzorców i praktyk samouczki w witrynie MSDN w [scenariuszy, wzorce i wskazówki dotyczące realizacji dla sieci Web usługi rozszerzeń (programu WSE) 3.0](https://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programowanie zabezpieczeń WCF opiera się na trzy kroki następujące ustawienie: tryb zabezpieczeń, typu poświadczeń klienta i wartości poświadczeń. Można wykonywać następujące czynności za pomocą kodu lub konfiguracji.  
  
## <a name="setting-the-security-mode"></a>Ustawianie trybu zabezpieczeń  
 Poniżej opisano ogólne kroki do programowania za pomocą tryb zabezpieczeń programu WCF:  
  
1.  Wybierz jeden z wstępnie zdefiniowanych powiązań odpowiednią do wymagań aplikacji. Aby uzyskać listę opcji powiązania, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md). Prawie każde powiązanie ma domyślnie włączoną obsługą zabezpieczeń. Jedynym wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding> klasy (przy użyciu konfiguracji [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Powiązanie, którą wybierzesz określa transportu. Na przykład <xref:System.ServiceModel.WSHttpBinding> korzysta z protokołu HTTP jako transportu; <xref:System.ServiceModel.NetTcpBinding> używa protokołu TCP.  
  
2.  Wybierz jeden z trybów zabezpieczeń dla wiązania. Należy pamiętać, że powiązanie, którą wybierzesz Określa tryb dostępne opcje. Na przykład <xref:System.ServiceModel.WSDualHttpBinding> nie zezwala na zabezpieczenia transportu (nie jest to opcja). Podobnie, ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umożliwia zabezpieczenie wiadomości.  
  
     Dostępne są trzy opcje:  
  
    1.  `Transport`  
  
         Zabezpieczenia transportu jest zależna od mechanizm, który używa powiązania, który wybrano. Na przykład, jeśli używasz `WSHttpBinding` mechanizmu zabezpieczeń jest Secure Sockets Layer (SSL) (również mechanizm dla protokołu HTTPS). Ogólnie rzecz biorąc główną zaletą zabezpieczeń transportu jest zapewnia dobre przepływność niezależnie od tego, które transportu używasz. Jednak mieć dwa ograniczenia: pierwszy to, że mechanizm transportu Określa typ poświadczenia używane do uwierzytelnienia użytkownika. Wadą jest tylko wtedy, gdy usługa musi współdziałać z innymi usługami, wymagających różne rodzaje poświadczeń. Drugą jest wartość, ponieważ nie zastosowano zabezpieczenia na poziomie komunikatu, są implementowane w sposób przeskoku przeskoku zamiast end-to-end. To ograniczenie ostatnim jest problemem, tylko wtedy, gdy ścieżka wiadomości między klientem a usługą zawiera pośredników. Aby uzyskać więcej informacji na temat które transportu do użycia, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aby uzyskać więcej informacji na temat za pomocą zabezpieczeń transportu zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         Zabezpieczenia komunikatów oznacza, że każdy komunikat zawiera niezbędne nagłówki i zabezpieczanie danych w celu przechowywania wiadomości. Ponieważ różni się w skład nagłówki może zawierać dowolną liczbę poświadczeń. To staje się czynnikiem, czy możesz się współdziałanie z innymi usługami zapotrzebowania typu poświadczenie, które nie udostępniają mechanizm transportu, czy komunikat może być używany z więcej niż jedna usługa, gdzie każda usługa wymaga typu różnych poświadczeń.  
  
         Aby uzyskać więcej informacji, zobacz [zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Ten wybór korzysta z warstwy transportowej do bezpiecznego transferu komunikatów, podczas każdej wiadomości zawiera bogaty poświadczenia muszą innych usług. To połączenie zalet wydajności zabezpieczenia transportu z zalet zaawansowanych poświadczenia zabezpieczeń wiadomości. Ta opcja jest dostępna w następujących powiązań: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, i <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Jeśli zdecydujesz się użyć zabezpieczeń transportu dla protokołu HTTP (innymi słowy, HTTPS), możesz skonfigurować hosta za pomocą certyfikatu SSL i Włącz protokół SSL na porcie. Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4.  Jeśli używasz <xref:System.ServiceModel.WSHttpBinding> i nie ma potrzeby ustanawiania sesji bezpiecznego, ustaw <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość `false`.  
  
     Bezpiecznej sesji występuje, gdy klient i usługa utworzyć kanał za pomocą klucza symetrycznego (klient i serwer, użyj tego samego klucza długości konwersacji, do czasu zamknięcia okna dialogowego).  
  
## <a name="setting-the-client-credential-type"></a>Ustawianie typu poświadczeń klienta  
 Wybieranie typu poświadczeń klienta zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Dostępne są następujące typy poświadczeń klienta:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 W zależności od tego, jak ustawić tryb należy ustawić typ poświadczeń. Na przykład, jeśli wybrano `wsHttpBinding`i ustawiono tryb "Message", a następnie można również ustawić `clientCredentialType` atrybut elementu komunikatu do jednej z następujących wartości: `None`, `Windows`, `UserName`, `Certificate` , a `IssuedToken`, jak pokazano w poniższym przykładzie konfiguracji.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 Lub w kodzie:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Ustawienie usługi poświadczeń wartości  
 Po wybraniu typu poświadczeń klienta, należy ustawić rzeczywiste poświadczenia dla usługi i klienta do używania. Usługi, poświadczenia są ustawiane przy użyciu <xref:System.ServiceModel.Description.ServiceCredentials> klasy i zwrócony przez <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwość <xref:System.ServiceModel.ServiceHostBase> klasy. Wiązanie używane oznacza typ poświadczeń usługi, wybrać tryb zabezpieczeń i typ poświadczeń klienta. Poniższy kod ustawia certyfikatu dla poświadczenia usługi.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Ustawienie wartości poświadczeń klienta  
 Na komputerze klienckim, ustaw wartości poświadczeń klienta przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy i zwrócony przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy. Poniższy kod ustawia certyfikatu jako poświadczenia na kliencie przy użyciu protokołu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
