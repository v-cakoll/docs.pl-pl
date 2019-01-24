---
title: '&lt;message&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b636a22fe7c6bcfae5b8f81c1566ea39c9f8ced5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683745"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;message&gt; w &lt;netMsmqBinding&gt;
Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP w tym `netMsmqBinding` powiązania.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netMsmqBinding>  
\<Powiązanie >  
\<security>  
\<message>  
  
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
|algorithmSuite|Ustawia komunikat algorytmów szyfrowania i klucz wrap, które są używane do uzyskania zabezpieczenia oparte na komunikatu dla komunikatów wysyłanych za pośrednictwem transportu MSMQ.<br /><br /> Wartość domyślna to `Aes256`. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta dla wiadomości wysłanych przez usługę transportową MSMQ. Prawidłowe wartości są następujące:<br /><br /> -Brak: Dzięki usłudze na współdziałanie z anonimowych klientów. Usługa ani klient wymaga poświadczeń.<br />-Windows: Dzięki temu wymiany protokołu SOAP i znajdować się w kontekście uwierzytelnionych poświadczeń Windows. To jest zawsze przeprowadza uwierzytelnianie za pomocą protokołu Kerberos.<br />— Nazwa użytkownika: Dzięki temu usługi wymagać który uwierzytelnienia klienta przy użyciu poświadczeń UserName. Poświadczenia w takim przypadku należy także określić przy użyciu `clientCredentials` zachowanie **Uwaga:**  Windows Communication Foundation (WCF) nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i rozpoczęcie używania te klucze dla zabezpieczenia wiadomości. Usługi WCF wymusza w związku z tym, że programu exchange jest zabezpieczone, korzystając z poświadczeń UserName. Ten tryb wymaga określenia certyfikatu usługi na po stronie klienta za pomocą `clientCredential` zachowanie i `serviceCertificate`. <br /><br /> -Certyfikat: Dzięki temu usługi wymagać który uwierzytelnienia klienta za pomocą certyfikatu. Poświadczeń klienta w tym przypadku musi być określona za pomocą `clientCredentials` zachowanie. Poświadczenia usługi w tym przypadku należy także określić przy użyciu `clientCredentials` zachowanie, określając `serviceCertificate`.<br />-CardSpace: Dzięki temu usługi wymagać, za pomocą CardSpace uwierzytelnienia klienta. `serviceCertiifcate` Musi być obsługiwana w `clientCredential` zachowanie.<br /><br /> Wartość domyślna to `Windows`. Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
