---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377758"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<Dodaj > z \<issuerChannelBehaviors >

Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z usługą STS.

> [!NOTE]
> Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie zgłoszony wyjątek.

\<system.ServiceModel>\
\<zachowania > \
sekcja endpointBehaviors \<zachowanie > \
\<clientCredentials>\
\<issuedToken > \
\<issuerChannelBehaviors > Element\
\<add>

## <a name="syntax"></a>Składnia

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|issuerAddress|Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.|
|behaviorConfiguration|Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Zawiera kolekcję zachowań punktu końcowego klienta usługi Windows Communication Foundation (WCF) ma być używany podczas komunikacji z określonej usługi tokenu usługi.|

## <a name="remarks"></a>Uwagi

`issuerAddress` zawiera identyfikator URI usługi tokenu zabezpieczającego, które klient chce się nawiązać połączenia z usługą. `behaviorConfiguration` Wskazuje zachowanie punktu końcowego, którego używa aplikacja w kanałach utworzone przez Windows Communication Foundation (WCF) można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Instrukcje: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
