---
title: <message> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736760"
---
# <a name="message-of-netmsmqbinding"></a>\<message> dla \<netMsmqBinding>

Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP dla tego `netMsmqBinding` powiązania.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a>Składnia

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|algorithmSuite|Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy, które są używane do uzyskania zabezpieczeń opartych na komunikatach wysyłanych za pośrednictwem transportu MSMQ.<br /><br /> Wartość domyślna to `Aes256`. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .|
|Powiązania ClientCredentialType|Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta dla wiadomości wysyłanych za pośrednictwem transportu MSMQ. Prawidłowe wartości to:<br /><br /> -Brak: umożliwia to usłudze współpracującie z anonimowymi klientami. Żadna usługa ani klient nie wymagają podania poświadczeń.<br />-Windows: umożliwia to wymianę protokołu SOAP w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows. Jest to zawsze wykonywane uwierzytelnianie oparte na protokole Kerberos.<br />-UserName: umożliwia usłudze wymaganie uwierzytelnienia klienta przy użyciu poświadczeń nazwy użytkownika. Poświadczenie w tym przypadku należy określić przy użyciu `clientCredentials` zachowania **ostrożności:** Windows Communication Foundation (WCF) nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów. W związku z tym WCF wymusza, aby program Exchange był zabezpieczony przy użyciu poświadczeń nazwy użytkownika. Ten tryb wymaga, aby certyfikat usługi był określony po stronie klienta przy użyciu `clientCredential` zachowań i `serviceCertificate` . <br /><br /> -Certificate: umożliwia usłudze wymaganie uwierzytelniania klienta przy użyciu certyfikatu. Poświadczenia klienta w tym przypadku należy określić przy użyciu `clientCredentials` zachowania. Poświadczenia usługi w tym przypadku należy określić przy użyciu `clientCredentials` zachowania przez określenie `serviceCertificate` .<br />-CardSpace: umożliwia usłudze wymaganie uwierzytelniania klienta przy użyciu programu CardSpace. `serviceCertificate`W zachowaniu musi być obsługiwana obsługa administracyjna `clientCredential` .<br /><br /> Wartość domyślna to `Windows`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType> .|

### <a name="child-elements"></a>Elementy podrzędne

Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
