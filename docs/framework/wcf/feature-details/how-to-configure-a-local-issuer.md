---
title: 'Instrukcje: Konfigurowanie lokalnego wystawcy'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90edf0735d890e0abc1560de5a7f523ee2faa7c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-local-issuer"></a>Instrukcje: Konfigurowanie lokalnego wystawcy
W tym temacie opisano sposób konfigurowania klienta do używania wystawcy lokalnego dla wystawionych tokenów.  
  
 Często gdy klient komunikuje się z usługi federacyjnej, usługi Określa adres zabezpieczeń używanych tokenu usługi, która oczekuje można wystawić tokenu klienta do samodzielnego uwierzytelnienia usługi federacyjnej. W niektórych sytuacjach klienta może być skonfigurowany do użycia *wystawcy lokalnego*.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]używa wystawcy lokalnego w przypadkach, gdy adres wystawcy wiązania federacyjnego jest http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous lub `null`. W takiej sytuacji należy skonfigurować <xref:System.ServiceModel.Description.ClientCredentials> adres wystawcy lokalnego i powiązania, które używają do komunikowania się z tym wystawcą.  
  
> [!NOTE]
>  Jeśli <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> właściwość `ClientCredentials` ustawiono klasy `true`, adres wystawcy lokalnego nie jest określony, a adres wystawcy określony przez [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub innych powiązania federacyjnego jest http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, lub jest `null`, następnie Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] wystawcy jest używany.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Aby skonfigurować wystawcy lokalnego w kodzie  
  
1.  Utwórz zmienną typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  Ustaw zmienną na wystąpienie zwrócony z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwość `ClientCredentials` klasy. To wystąpienie jest zwracany przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwości klienta (dziedziczone z <xref:System.ServiceModel.ClientBase%601>) lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> właściwości <xref:System.ServiceModel.ChannelFactory>:  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> właściwości nowe wystąpienie klasy <xref:System.ServiceModel.EndpointAddress>, adres wystawcy lokalnego jako argument do konstruktora.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Można również utworzyć nową <xref:System.Uri> wystąpienie jako argument do konstruktora.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders` Parametr jest tablicą <xref:System.ServiceModel.Channels.AddressHeader> wystąpień, jak pokazano.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  Ustaw powiązanie wystawcy lokalnego przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> właściwości.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  Opcjonalny. Dodawanie zachowania punktu końcowego skonfigurowanego dla wystawcy lokalnego przez dodanie takiego zachowania do kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> właściwości.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Aby skonfigurować wystawcy lokalnego w konfiguracji  
  
1.  Utwórz [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element jako element podrzędny [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element, który jest elementem podrzędnym [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element zachowanie punktu końcowego.  
  
2.  Ustaw `address` atrybutu adres wystawcy lokalnego, która będzie akceptować żądania tokenu.  
  
3.  Ustaw `binding` i `bindingConfiguration` atrybuty do wartości, które odwołują się do powiązania odpowiednie do użycia przy komunikacji z punktem końcowym wystawcy lokalnego.  
  
4.  Opcjonalny. Ustaw [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element jako element podrzędny <`localIssuer`> element i określ informacje o tożsamości wystawcy lokalnego.  
  
5.  Opcjonalny. Ustaw [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element jako element podrzędny <`localIssuer`> element i określ dodatkowych nagłówków, które są wymagane do prawidłowego adresowania wystawcy lokalnego.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Należy pamiętać o tym, czy jeśli wystawcy adres i powiązanie zostały określone dla danego powiązania, wystawcy lokalnego nie jest używany przez punkty końcowe korzystające z tego wiązania. Klienci, którzy oczekują, że zawsze używaj wystawcy lokalnego powinien upewnij się, że nie używaj takiego powiązania lub czy zmodyfikuj powiązanie, tak aby adres wystawcy jest `null`.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Porady: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Porady: tworzenie WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
