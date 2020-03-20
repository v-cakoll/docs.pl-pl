---
title: <transport> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152934"
---
# <a name="transport-of-netmsmqbinding"></a>\<> transportowy \<netMsmqBinding>
Definiuje ustawienia zabezpieczeń transportu.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>bezpieczeństwa**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>transportowe**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Msmqauthenticationmode|Określa sposób uwierzytelniania wiadomości przez transport usługi MSMQ. Prawidłowe wartości są następujące:<br /><br /> - Brak: Brak uwierzytelniania.<br />- WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory do pobierania certyfikatu X.509 dla identyfikatora zabezpieczeń skojarzonego z wiadomością. Jest to następnie używane do sprawdzania listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu dla kolejki.<br />- Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to `WindowsDomain`.<br /><br /> Jeśli ten atrybut jest `None`ustawiony `msmqProtectionLevel` na , atrybut `None`musi być również ustawiony na . Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Określa algorytm, który ma być używany do szyfrowania wiadomości w sieci podczas przesyłania wiadomości między menedżerami kolejek komunikatów. Prawidłowe wartości są następujące:<br /><br /> - RC4Stream<br />- AES<br />- Wartość domyślna to `RC4Stream`. Ten atrybut jest <xref:System.ServiceModel.MsmqEncryptionAlgorithm>typu .|  
|Msmqprotectionlevel|Określa sposób, w jaki wiadomości są zabezpieczone na poziomie transportu usługi MSMQ. Szyfrowanie zapewnia integralność wiadomości, podczas gdy podpisywanie i szyfrowanie zapewnia integralność wiadomości i nie odrzucenie. Oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca jest tym, kim mówią, że są. Prawidłowe wartości są następujące:<br /><br /> - Brak: Brak ochrony.<br />- Podpisz: Wiadomości są podpisane.<br />- EncryptAndSign: Wiadomości są szyfrowane i podpisane.<br />- Wartość `Sign`domyślna to .|  
|msmqSecureHashAlgorithm|Określa algorytm mieszania, który ma być używany do obliczania skrótu wiadomości. Prawidłowe wartości są następujące:<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> Wartość domyślna to `SHA1`. Ten atrybut jest <xref:System.ServiceModel.MsmqSecureHashAlgorithm>typu .<br>Ze względu na problemy z kolizją z MD5 i SHA1 firma Microsoft zaleca sha256 lub lepsze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>bezpieczeństwa](security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń transportu dla transportów w kolejce.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<wiążące>](bindings.md)
