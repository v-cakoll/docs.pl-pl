---
title: <issuerChannelBehaviors>, element
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929928"
---
# <a name="issuerchannelbehaviors-element"></a>\<issuerChannelBehaviors, element >

Zawiera kolekcję zachowań punktu końcowego klienta w programie Windows Communication Foundation (w ramach konfiguracji), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi. Zdefiniowane zachowania nie mogą zawierać żadnych [ \<elementów ClientCredentials >](clientcredentials.md) .

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a>Składnia

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|Dodaje zachowanie do kolekcji.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<issuedToken >](issuedtoken.md)|Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.|

## <a name="remarks"></a>Uwagi

Użyj tego elementu, gdy do komunikacji z usługą należy używać wszelkich `<clientCredentials>` zachowań (oprócz zachowań zawierających elementy). Na przykład jeśli [ \<element zachowań > DataContractSerializer](datacontractserializer-element.md) musi być uwzględniony.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Uwierzytelnianie i tożsamość usług](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Instrukcje: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
