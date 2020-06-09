---
title: 'Instrukcje: Konfigurowanie lokalnego wystawcy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601247"
---
# <a name="how-to-configure-a-local-issuer"></a>Instrukcje: Konfigurowanie lokalnego wystawcy

W tym temacie opisano sposób konfigurowania klienta do używania lokalnego wystawcy dla wystawionych tokenów.

Często, gdy klient komunikuje się z usługą federacyjną, usługa określa adres usługi tokenu zabezpieczającego, która powinna wydać token używany przez klienta do samodzielnego uwierzytelnienia w usłudze federacyjnej. W niektórych sytuacjach klient może być skonfigurowany do korzystania z *lokalnego wystawcy*.

Windows Communication Foundation (WCF) używa wystawcy lokalnego w przypadkach, gdy adres wystawcy powiązania federacyjnego to `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null` . W takich przypadkach należy skonfigurować <xref:System.ServiceModel.Description.ClientCredentials> program przy użyciu adresu wystawcy lokalnego i powiązania, które ma być używane do komunikacji z tym wystawcą.

> [!NOTE]
> Jeśli <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> Właściwość `ClientCredentials` klasy jest ustawiona na `true` , adres wystawcy lokalnego nie zostanie określony, a adres wystawcy określony przez [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub inne powiązanie federacyjne to `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` , `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` , lub jest `null` , używany jest wystawca programu Windows CardSpace.

## <a name="to-configure-the-local-issuer-in-code"></a>Aby skonfigurować wystawcy lokalnego w kodzie

1. Utwórz zmienną typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>

2. Ustaw zmienną na wystąpienie zwracane z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwości `ClientCredentials` klasy. To wystąpienie jest zwracane przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość klienta (dziedziczone z <xref:System.ServiceModel.ClientBase%601> ) lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość <xref:System.ServiceModel.ChannelFactory> :

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> Właściwość na nowe wystąpienie elementu <xref:System.ServiceModel.EndpointAddress> , z adresem wystawcy lokalnego jako argumentem konstruktora.

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     Alternatywnie Utwórz nowe <xref:System.Uri> wystąpienie jako argument konstruktora.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     `addressHeaders`Parametr jest tablicą <xref:System.ServiceModel.Channels.AddressHeader> wystąpień, jak pokazano.

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. Ustaw powiązanie dla wystawcy lokalnego przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> właściwości.

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. Opcjonalny. Dodaj skonfigurowane zachowania punktu końcowego dla wystawcy lokalnego przez dodanie takich zachowań do kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> Właściwość.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Aby skonfigurować wystawcę lokalnego w konfiguracji

1. Utwórz [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element jako obiekt podrzędny [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) elementu, który jest elementem podrzędnym [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) elementu w zachowaniu punktu końcowego.

2. Ustaw wartość `address` atrybutu na adres wystawcy lokalnego, która będzie akceptować żądania tokenów.

3. Ustaw `binding` atrybuty i `bindingConfiguration` na wartości, które odwołują się do odpowiedniego powiązania do użycia podczas komunikacji z punktem końcowym wystawcy lokalnego.

4. Opcjonalny. Ustaw [\<identity>](../../configure-apps/file-schema/wcf/identity.md) jako element podrzędny <`localIssuer` elementu> i Określ informacje o tożsamości dla wystawcy lokalnego.

5. Opcjonalny. Ustaw [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element jako obiekt podrzędny <`localIssuer` elementu> i określ dodatkowe nagłówki, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego.

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Należy pamiętać, że jeśli dla danego powiązania określono adres wystawcy i powiązanie, wystawcy lokalnego nie jest używany dla punktów końcowych używających tego powiązania. Klienci, którzy oczekują zawsze używać wystawcy lokalnego, powinni upewnić się, że nie używają takiego powiązania lub że modyfikują powiązanie, tak aby adres wystawcy był `null` .

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: tworzenie klienta federacyjnego](how-to-create-a-federated-client.md)
- [Instrukcje: tworzenie elementu WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
