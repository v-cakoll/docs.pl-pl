---
title: <transport> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152934"
---
# <a name="transport-of-netmsmqbinding"></a>\<transport> dla \<netMsmqBinding>
Definiuje ustawienia zabezpieczeń transportu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
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
|msmqAuthenticationMode|Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ. Prawidłowe wartości to:<br /><br /> -Brak: brak uwierzytelniania.<br />-WindowsDomain: mechanizm uwierzytelniania używa Active Directory, aby pobrać certyfikat X. 509 dla identyfikatora zabezpieczeń skojarzonego z wiadomością. Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienie do zapisu dla kolejki.<br />-Certificate: kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to `WindowsDomain`.<br /><br /> Jeśli ten atrybut jest ustawiony na `None` , `msmqProtectionLevel` atrybut musi również być ustawiony na `None` . Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości. Prawidłowe wartości to:<br /><br /> - RC4Stream<br />-AES<br />— Wartość domyślna to `RC4Stream` . Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .|  
|msmqProtectionLevel|Określa sposób, w jaki komunikaty są zabezpieczane na poziomie transportu usługi MSMQ. Szyfrowanie zapewnia integralność komunikatów, podczas gdy podpisywanie i szyfrowanie zapewnia integralność komunikatów i odrzucanie. Oznacza to, że komunikat rzeczywiście pochodzi od nadawcy, a nadawca wskazuje, że są. Prawidłowe wartości to:<br /><br /> -Brak: brak ochrony.<br />-Sign: komunikaty są podpisane.<br />-EncryptAndSign: komunikaty są szyfrowane i podpisane.<br />-Wartość domyślna to `Sign` .|  
|msmqSecureHashAlgorithm|Określa algorytm wyznaczania wartości skrótu, który ma być używany do obliczania skrótu wiadomości. Prawidłowe wartości to:<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> Wartość domyślna to `SHA1`. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .<br>Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń transportu dla transportów umieszczonych w kolejce.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
