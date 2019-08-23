---
title: <add> dla <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920114"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<Dodawanie > \<issuerChannelBehaviors >

Dodaje zachowanie punktu końcowego, które ma być używane podczas komunikacji z usługą STS.

> [!NOTE]
> Jeśli dowolne zachowanie punktu końcowego zawiera [ \<element ClientCredentials >](clientcredentials.md) , zostanie zgłoszony wyjątek.

\<system.ServiceModel>\
\<zachowania > \
> zachowanie \<sekcji endpointBehaviors \
\<clientCredentials>\
\<issuedToken > \
\<issuerChannelBehaviors > element \
\<add>

## <a name="syntax"></a>Składnia

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|issuerAddress|Identyfikator URI wystawcy tokenu zabezpieczającego do komunikacji.|
|behaviorConfiguration|Nazwa zachowania punktu końcowego zdefiniowana w tym samym pliku konfiguracyjnym.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<issuerChannelBehaviors >](issuerchannelbehaviors-element.md)|Zawiera kolekcję zachowań punktu końcowego klienta programu Windows Communication Foundation (WCF), które mają być używane podczas komunikowania się z określonymi usługami tokenu usługi.|

## <a name="remarks"></a>Uwagi

`issuerAddress`zawiera identyfikator URI usługi tokenu zabezpieczającego, z którą klient chce się skomunikować. `behaviorConfiguration`wskazuje zachowanie punktu końcowego, którego aplikacja używa w kanałach utworzonych przez Windows Communication Foundation (WCF) do pobierania wystawionych tokenów z usług tokenów zabezpieczających.

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
- [\<issuerChannelBehaviors >](issuerchannelbehaviors-element.md)
