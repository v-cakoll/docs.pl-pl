---
title: Programowanie zabezpieczeń WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3eb645dcc5b8cc1c52818e290699ebadcd0943c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="programming-wcf-security"></a>Programowanie zabezpieczeń WCF
W tym temacie opisano podstawowe zadania programowania, używany do tworzenia bezpiecznego aplikacji Windows Communication Foundation (WCF). W tym temacie omówiono tylko uwierzytelnianie, poufność i integralność, nazywanych zbiorczo *transferu zabezpieczeń*. W tym temacie nie opisano autoryzacji (kontrola dostępu do zasobów lub usług); informacje dotyczące autoryzacji znajdują się w temacie [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Wprowadzenie przydatna do pojęć związanych z zabezpieczeniami, zwłaszcza w odniesieniu do usługi WCF, zobacz zbiór samouczki wzorców i rozwiązań w witrynie MSDN w [scenariuszy, wzorców i wskazówki dotyczące implementacji dla sieci Web usług ulepszenia (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programowanie zabezpieczeń WCF opiera się na trzy kroki następujące ustawienia: tryb zabezpieczeń, typu poświadczeń klienta i wartości poświadczeń. Można wykonywać następujące czynności, za pomocą kodu lub konfiguracji.  
  
## <a name="setting-the-security-mode"></a>Ustawianie trybu zabezpieczeń  
 Poniżej opisano ogólne kroki do programowania za pomocą trybu zabezpieczeń w programie WCF:  
  
1.  Wybierz jeden z wstępnie zdefiniowanych powiązań odpowiednią do wymagań aplikacji. Listę dostępnych opcji Powiązanie zawiera [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md). Domyślnie niemal każde powiązanie ma włączoną obsługą zabezpieczeń. Jedynym wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding> klasy (za pomocą konfiguracji, [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Wybrane powiązanie określa transportu. Na przykład <xref:System.ServiceModel.WSHttpBinding> korzysta z protokołu HTTP jako transportu; <xref:System.ServiceModel.NetTcpBinding> protokołu TCP.  
  
2.  Wybierz jeden z trybów zabezpieczeń dla powiązania. Należy pamiętać, że wybrane powiązanie Określa tryb dostępnych opcji. Na przykład <xref:System.ServiceModel.WSDualHttpBinding> nie zezwala na zabezpieczeń transportu (nie jest ona opcję). Podobnie, ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umożliwia zabezpieczeń wiadomości.  
  
     Wyświetlane są trzy opcje:  
  
    1.  `Transport`  
  
         Zabezpieczenia transportu zależy od mechanizm, który używa wybranego powiązania. Na przykład, jeśli używasz `WSHttpBinding` mechanizm zabezpieczeń jest Secure Sockets Layer (SSL) (również mechanizm dla protokołu HTTPS). Główną zaletą zabezpieczeń transportu jest ogólnie rzecz biorąc, zapewnia dobre przepływności, niezależnie od tego, które transportu są używane. Jednak mieć dwa ograniczenia: pierwsza to, że mechanizm transportu nakazują typ poświadczenia używane do uwierzytelnienia użytkownika. Wadą jest tylko wtedy, gdy usługa musi współdziałać z innymi usługami, które wymagają różnych rodzajów poświadczeń. Drugim jest, ponieważ nie zastosowano zabezpieczenia na poziomie komunikatu, zabezpieczeń jest zaimplementowana w sposób przeskoku przeskoku zamiast end-to-end. To ograniczenie ostatnie jest problem tylko, jeśli ścieżka wiadomości między klientem a usługą zawiera pośredników. Aby uzyskać więcej informacji o którym transportu do użycia, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aby uzyskać więcej informacji o korzystaniu z zabezpieczeń transportu, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         Zabezpieczenia komunikatów oznacza, że każdy komunikat zawiera niezbędne nagłówki i bezpieczeństwo danych, aby zachować wiadomości. Ponieważ kompozycji nagłówki różni się może zawierać dowolną liczbę poświadczeń. To staje się czynnikiem, czy możesz są współdziałanie z innymi usługami tego żądanie typu poświadczenie mechanizm transportu nie może dostarczyć, czy wiadomości musi być używany z więcej niż jedna usługa, gdzie każda usługa wymaga typu różnych poświadczeń.  
  
         Aby uzyskać więcej informacji, zobacz [zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Ten wybór używa Warstwa transportu do bezpiecznego transferu komunikatów, podczas każdej wiadomości zawiera bogaty poświadczenia muszą innych usług. Łączy wydajności zaletą zabezpieczeń transportu i zalety zaawansowanych poświadczenia zabezpieczeń wiadomości. To ustawienie jest dostępne z powiązaniami następujących: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, i <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Jeśli zdecydujesz się użyć zabezpieczeń transportu dla protokołu HTTP (innymi słowy, HTTPS), należy również skonfigurować hosta za pomocą certyfikatu SSL i Włącz protokół SSL na porcie. Aby uzyskać więcej informacji, zobacz [zabezpieczeń transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4.  Jeśli używasz <xref:System.ServiceModel.WSHttpBinding> i nie ma potrzeby nawiązywania bezpiecznej sesji, należy ustawić <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwości `false`.  
  
     Bezpieczna sesja występuje, gdy klient i usługa utworzyć kanał za pomocą klucza symetrycznego (klient i serwer używać tego samego klucza długości konwersację, do czasu zamknięcia okna dialogowego).  
  
## <a name="setting-the-client-credential-type"></a>Ustawienie typu poświadczeń klienta  
 Wybierz typ poświadczeń klienta zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Dostępne są następujące typy poświadczeń klienta:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 W zależności od tego, jak możesz ustawić tryb należy ustawić typ poświadczeń. Na przykład, jeśli wybrano `wsHttpBinding`, ustawiono tryb "Komunikat", a następnie można również ustawić `clientCredentialType` atrybut elementu wiadomości do jednej z następujących wartości: `None`, `Windows`, `UserName`, `Certificate` , a `IssuedToken`, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
 Po wybraniu typu poświadczeń klienta, należy ustawić rzeczywiste poświadczenia dla usługi i klienta do używania. W usłudze, poświadczenia są ustawiane przy użyciu <xref:System.ServiceModel.Description.ServiceCredentials> klasy i zwrócony przez <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwość <xref:System.ServiceModel.ServiceHostBase> klasy. Używane powiązanie oznacza typ poświadczeń usługi, wybrany tryb zabezpieczeń i typu poświadczeń klienta. Poniższy kod ustawia certyfikatu dla poświadczenia usługi.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Ustawienie wartości poświadczeń klienta  
 Na komputerze klienckim, należy ustawić wartości poświadczeń klienta przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy i zwrócony przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy. Poniższy kod ustawia certyfikatu jako poświadczeń klienta przy użyciu protokołu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
