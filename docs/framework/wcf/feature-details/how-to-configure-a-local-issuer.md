---
title: 'Instrukcje: konfigurowanie lokalnego wystawcy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972067"
---
# <a name="how-to-configure-a-local-issuer"></a>Instrukcje: konfigurowanie lokalnego wystawcy

W tym temacie opisano sposób konfigurowania klienta do używania lokalnego wystawcy dla wystawionych tokenów.

Często, gdy klient komunikuje się z usługą federacyjną, usługa określa adres usługi tokenu zabezpieczającego, która powinna wydać token używany przez klienta do samodzielnego uwierzytelnienia w usłudze federacyjnej. W niektórych sytuacjach klient może być skonfigurowany do korzystania z *lokalnego*wystawcy.

Windows Communication Foundation (WCF) używa wystawcy lokalnego w przypadkach, gdy adres wystawcy powiązania federacyjnego `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` to `null`lub. W takich przypadkach należy skonfigurować <xref:System.ServiceModel.Description.ClientCredentials> program przy użyciu adresu wystawcy lokalnego i powiązania, które ma być używane do komunikacji z tym wystawcą.

> [!NOTE]
> `true`Jeśli właściwość klasy`ClientCredentials` jest ustawiona na, adres wystawcy lokalnego nie zostanie określony [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) , a adres wystawcy określony przez WSFederationHttpBinding > lub inne powiązanie federacyjne to <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, lub jest `null`, używany jest wystawca programu Windows CardSpace.

## <a name="to-configure-the-local-issuer-in-code"></a>Aby skonfigurować wystawcy lokalnego w kodzie

1. Utwórz zmienną typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>

2. Ustaw zmienną na wystąpienie zwracane z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwości `ClientCredentials` klasy. To wystąpienie <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> jest zwracane przez właściwość klienta (dziedziczone z <xref:System.ServiceModel.ClientBase%601>) <xref:System.ServiceModel.ChannelFactory>lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość:

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Ustaw właściwość na nowe wystąpienie <xref:System.ServiceModel.EndpointAddress>elementu, z adresem wystawcy lokalnego jako argumentem konstruktora. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     Alternatywnie Utwórz nowe <xref:System.Uri> wystąpienie jako argument konstruktora.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     Parametr jest tablicą <xref:System.ServiceModel.Channels.AddressHeader>wystąpień `addressHeaders` , jak pokazano.

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. Ustaw powiązanie dla wystawcy lokalnego przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> właściwości.

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. Opcjonalny. Dodaj skonfigurowane zachowania punktu końcowego dla wystawcy lokalnego przez dodanie takich zachowań do kolekcji zwróconej <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> przez właściwość.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Aby skonfigurować wystawcę lokalnego w konfiguracji

1. Utwórz element [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) LocalIssuer > jako obiekt podrzędny elementu issuedToken >, który jest samym elementem podrzędnym elementu ClientCredentials > w zachowaniu punktu końcowego. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)

2. Ustaw wartość `address` atrybutu na adres wystawcy lokalnego, która będzie akceptować żądania tokenów.

3. Ustaw atrybuty `bindingConfiguration` i na wartości, które odwołują się do odpowiedniego powiązania do użycia podczas komunikacji z punktem końcowym wystawcy lokalnego. `binding`

4. Opcjonalna. Ustaw >`localIssuer`tożsamość elementu jako element podrzędny < > elementu i Określ informacje o tożsamości dla wystawcy lokalnego. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

5. Opcjonalny. `localIssuer` [ Ustawnagłówki>elementujakoelementpodrzędny<>elementuiokreśldodatkowenagłówki,któresąwymaganewceluprawidłowegoadresowania\<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) wystawcy lokalnego.

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Należy pamiętać, że jeśli dla danego powiązania określono adres wystawcy i powiązanie, wystawcy lokalnego nie jest używany dla punktów końcowych używających tego powiązania. Klienci, którzy oczekują zawsze używać wystawcy lokalnego, powinni upewnić się, że nie używają takiego powiązania lub że modyfikują powiązanie, tak aby adres `null`wystawcy był.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Instrukcje: Utwórz WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
