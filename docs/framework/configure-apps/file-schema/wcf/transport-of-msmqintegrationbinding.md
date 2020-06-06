---
title: <transport> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152960"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<transport> dla \<msmqIntegrationBinding>
Definiuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ. Jeśli jest ustawiona na `None` , wartość `msmqProtectionLevel` atrybutu musi również być ustawiona na `None` .<br /><br /> Prawidłowe wartości to:<br /><br /> -Brak: brak uwierzytelniania.<br />-WindowsDomain: mechanizm uwierzytelniania używa Active Directory, aby uzyskać certyfikat X. 509 dla identyfikatora SID skojarzonego z wiadomością. Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu w kolejce.<br />-Certificate: kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to WindowsDomain. Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode> .|  
|`msmqEncryptionAlgorithm`|Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości. Prawidłowe wartości to:<br /><br /> - RC4Stream<br />-AES<br /><br /> Wartość domyślna to RC4Stream. Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .|  
|`msmqProtectionLevel`|Określa, w jaki sposób wiadomość jest zabezpieczona na poziomie transportu usługi MSMQ. Szyfrowanie zapewnia integralność komunikatów, podczas gdy EncryptAndSign zapewnia integralność komunikatów i odrzucanie. oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca to osoba, której mówią.<br /><br /> -Prawidłowe wartości są następujące:<br />-Brak: brak ochrony.<br />-Sign: komunikaty są podpisane.<br />-EncryptAndSign: komunikaty są szyfrowane i podpisane.<br /><br /> Wartość domyślna to Sign. Ten atrybut jest typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|-Określa algorytm, który ma być używany podczas obliczania skrótu jako części podpisów. Prawidłowe wartości to:<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> Wartość domyślna to SHA1. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .<br>Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element hermetyzuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów. Te ustawienia są takie same dla integracji usługi kolejkowania komunikatów i transportów znajdujących się w kolejce. Umożliwia ustawienie trybu uwierzytelniania, algorytmu szyfrowania, algorytmu bezpiecznego skrótu i poziomu ochrony.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
