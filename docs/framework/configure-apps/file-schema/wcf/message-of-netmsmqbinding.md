---
title: <message> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931514"
---
# <a name="message-of-netmsmqbinding"></a>\<> \<komunikatu usługi msmqbinding >

Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP dla tego `netMsmqBinding` powiązania.

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

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
|algorithmSuite|Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy, które są używane do uzyskania zabezpieczeń opartych na komunikatach wysyłanych za pośrednictwem transportu MSMQ.<br /><br /> Wartość domyślna to `Aes256`. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|
|clientCredentialType|Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta dla wiadomości wysyłanych za pośrednictwem transportu MSMQ. Prawidłowe wartości to:<br /><br /> Dawaj Dzięki temu usługa może korzystać z anonimowych klientów. Żadna usługa ani klient nie wymagają podania poświadczeń.<br />Systemy Dzięki temu wymiana protokołu SOAP będzie odbywać się w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows. Jest to zawsze wykonywane uwierzytelnianie oparte na protokole Kerberos.<br />Uż Dzięki temu usługa musi wymagać uwierzytelnienia klienta przy użyciu poświadczeń nazwy użytkownika. Poświadczenie w tym przypadku należy określić przy użyciu `clientCredentials` zachowania **ostrożności:**  Windows Communication Foundation (WCF) nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów. W związku z tym WCF wymusza, aby program Exchange był zabezpieczony przy użyciu poświadczeń nazwy użytkownika. Ten tryb wymaga, aby certyfikat usługi był określony po stronie klienta przy użyciu `clientCredential` zachowań i `serviceCertificate`. <br /><br /> Certyfikatu Dzięki temu usługa musi wymagać uwierzytelnienia klienta przy użyciu certyfikatu. Poświadczenia klienta w tym przypadku należy określić przy użyciu `clientCredentials` zachowania. Poświadczenia usługi w tym przypadku należy określić przy użyciu `clientCredentials` zachowania przez `serviceCertificate`określenie.<br />CardSpace Dzięki temu usługa musi wymagać uwierzytelnienia klienta przy użyciu programu CardSpace. W zachowaniu `serviceCertificate` musi być obsługiwana `clientCredential` obsługa administracyjna.<br /><br /> Wartość domyślna to `Windows`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|

### <a name="child-elements"></a>Elementy podrzędne

Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<> zabezpieczeń](security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|

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
- [\<> powiązania](../../../misc/binding.md)
