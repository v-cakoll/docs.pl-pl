---
title: Programowanie zabezpieczeń WCF
description: Dowiedz się, jak utworzyć bezpieczną aplikację WCF, w tym uwierzytelnianie, poufność i integralność.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 8e77c667dd8904c10bbab88e1413690677cef53b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244988"
---
# <a name="programming-wcf-security"></a>Programowanie zabezpieczeń WCF
W tym temacie opisano podstawowe zadania programistyczne służące do tworzenia aplikacji Secure Windows Communication Foundation (WCF). W tym temacie omówiono jedynie uwierzytelnianie, poufność i integralność, nazywane zbiorczo *zabezpieczeniami transferu*. Ten temat nie obejmuje autoryzacji (kontrola dostępu do zasobów lub usług); Aby uzyskać informacje na temat autoryzacji, zobacz [autoryzacja](authorization-in-wcf.md).  
  
> [!NOTE]
> Aby dowiedzieć się więcej na temat pojęć związanych z zabezpieczeniami, szczególnie w odniesieniu do usługi WCF, zobacz zestaw samouczków i rozwiązań w witrynie MSDN w oparciu o [scenariusze, wzorce i wskazówki dotyczące implementacji dla ulepszeń usług sieci Web (WSE) 3,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).  
  
 Programowanie zabezpieczeń WCF opiera się na trzech krokach: tryb zabezpieczeń, typ poświadczeń klienta oraz wartości poświadczeń. Kroki te można wykonać za pomocą kodu lub konfiguracji.  
  
## <a name="setting-the-security-mode"></a>Ustawianie trybu zabezpieczeń  
 Poniżej objaśniono ogólne kroki programowania z trybem zabezpieczeń w programie WCF:  
  
1. Wybierz jedno ze wstępnie zdefiniowanych powiązań odpowiednie dla wymagań aplikacji. Aby uzyskać listę opcji powiązań, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md). Domyślnie niemal każde powiązanie ma włączone zabezpieczenia. Jedynym wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding> Klasa (przy użyciu konfiguracji, a [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).  
  
     Wybrane powiązanie określa transport. Na przykład <xref:System.ServiceModel.WSHttpBinding> używa protokołu HTTP jako transportu; <xref:System.ServiceModel.NetTcpBinding> używa protokołu TCP.  
  
2. Wybierz jeden z trybów zabezpieczeń dla powiązania. Należy zauważyć, że wybrane powiązanie określa dostępne opcje trybu. Na przykład nie <xref:System.ServiceModel.WSDualHttpBinding> zezwala na zabezpieczenia transportu (nie jest to opcja). Analogicznie, ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> <xref:System.ServiceModel.NetNamedPipeBinding> zabezpieczenia komunikatów.  
  
     Masz trzy opcje:  
  
    1. `Transport`  
  
         Zabezpieczenia transportu są zależne od mechanizmu wybranego przez Ciebie powiązania. Na przykład, jeśli używasz, `WSHttpBinding` mechanizm zabezpieczeń jest SSL (SSL) (również mechanizm protokołu HTTPS). Ogólnie mówiąc, główną zaletą zabezpieczeń transportu jest to, że zapewnia ona dobrą przepływność niezależnie od używanego transportu. Jednak ma dwa ograniczenia: Pierwszy polega na tym, że mechanizm transportu wymusza typ poświadczeń używany do uwierzytelniania użytkownika. Jest to wadą tylko wtedy, gdy usługa musi współpracować z innymi usługami, które wymagają różnych typów poświadczeń. Drugim jest to, że ze względu na to, że zabezpieczenia nie są stosowane na poziomie komunikatu, zabezpieczenia są implementowane w sposób przeskokowy, a nie na kompletny. Ten ostatni problem występuje tylko wtedy, gdy ścieżka komunikatu między klientem a usługą obejmuje pośredników. Aby uzyskać więcej informacji o tym, który transport ma być używany, zobacz [Wybieranie transportu](choosing-a-transport.md). Aby uzyskać więcej informacji o korzystaniu z zabezpieczeń transportu, zobacz [Omówienie zabezpieczeń transportu](transport-security-overview.md).  
  
    2. `Message`  
  
         Zabezpieczenia komunikatów oznacza, że każdy komunikat zawiera niezbędne nagłówki i dane, aby zachować komunikat bezpieczny. Ponieważ kompozycja nagłówków jest różna, można dołączyć dowolną liczbę poświadczeń. Jest to czynnik, jeśli pracujesz z innymi usługami, które wymagają określonego typu poświadczeń, których mechanizm transportu nie może dostarczyć, lub jeśli komunikat musi być używany z więcej niż jedną usługą, gdzie każda usługa wymaga innego typu poświadczeń.  
  
         Aby uzyskać więcej informacji, zobacz [zabezpieczenia komunikatów](message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Ten wybór używa warstwy transportu do zabezpieczenia transferu wiadomości, podczas gdy każdy komunikat zawiera zaawansowane poświadczenia, które są wymagane przez inne usługi. Obejmuje to zalety wydajności transportu z wykorzystaniem bogatych poświadczeń w zakresie zabezpieczeń komunikatów. Jest on dostępny z następującymi powiązaniami: <xref:System.ServiceModel.BasicHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> , <xref:System.ServiceModel.NetPeerTcpBinding> i <xref:System.ServiceModel.WSHttpBinding> .  
  
3. Jeśli zdecydujesz się korzystać z zabezpieczeń transportu dla protokołu HTTP (innymi słowy, HTTPS), należy również skonfigurować hosta z certyfikatem SSL i włączyć protokół SSL na porcie. Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](http-transport-security.md).  
  
4. Jeśli używasz usługi <xref:System.ServiceModel.WSHttpBinding> i nie musisz ustanawiać bezpiecznej sesji, ustaw <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> Właściwość na wartość `false` .  
  
     Bezpieczna sesja odbywa się, gdy klient i usługa tworzą kanał przy użyciu klucza symetrycznego (zarówno klient, jak i serwer używają tego samego klucza dla długości konwersacji, dopóki okno dialogowe nie zostanie zamknięte).  
  
## <a name="setting-the-client-credential-type"></a>Ustawianie typu poświadczeń klienta  
 W razie potrzeby wybierz odpowiedni typ poświadczeń klienta. Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](selecting-a-credential-type.md). Dostępne są następujące typy poświadczeń klienta:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 W zależności od sposobu ustawienia trybu należy ustawić typ poświadczenia. Na przykład jeśli wybrano `wsHttpBinding` i ustawisz tryb na "Message", można również ustawić `clientCredentialType` atrybut elementu Message na jedną z następujących wartości: `None` , `Windows` ,, `UserName` `Certificate` , i `IssuedToken` , jak pokazano w poniższym przykładzie konfiguracji.  
  
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
 Po wybraniu typu poświadczeń klienta należy ustawić rzeczywiste poświadczenia usługi i klienta, które mają być używane. W usłudze poświadczenia są ustawiane za pomocą <xref:System.ServiceModel.Description.ServiceCredentials> klasy i zwracane przez <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Właściwość <xref:System.ServiceModel.ServiceHostBase> klasy. Powiązanie w użyciu sugeruje typ poświadczeń usługi, wybrany tryb zabezpieczeń i typ poświadczenia klienta. Poniższy kod ustawia certyfikat dla poświadczenia usługi.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Ustawianie wartości poświadczeń klienta  
 Na kliencie Ustaw wartości poświadczeń klienta przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy i zwrócone przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość <xref:System.ServiceModel.ClientBase%601> klasy. Poniższy kod służy do ustawiania certyfikatu jako poświadczenia na kliencie przy użyciu protokołu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Podstawy programowania przy użyciu programu WCF](../basic-wcf-programming.md)
- [Typowe scenariusze zabezpieczeń](common-security-scenarios.md)
