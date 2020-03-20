---
title: <transport> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152960"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<> transportowy \<msmqIntegrationBinding>
Definiuje ustawienia zabezpieczeń dla transportu integracji Usługi kolejkowania wiadomości.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>bezpieczeństwa**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>transportowe**  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Określa sposób uwierzytelniania wiadomości przez transport usługi MSMQ. Jeśli jest ustawiona na `None`wartość `msmqProtectionLevel` , wartość atrybutu `None`musi być również ustawiona na .<br /><br /> Prawidłowe wartości są następujące:<br /><br /> - Brak: Brak uwierzytelniania.<br />- WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory, aby uzyskać certyfikat X.509 dla identyfikatora SID skojarzonego z wiadomością. Jest to następnie używane do sprawdzania listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu w kolejce.<br />- Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartością domyślną jest WindowsDomain. Ten atrybut jest <xref:System.ServiceModel.MsmqAuthenticationMode>typu .|  
|`msmqEncryptionAlgorithm`|Określa algorytm, który ma być używany do szyfrowania wiadomości w sieci podczas przesyłania wiadomości między menedżerami kolejek komunikatów. Prawidłowe wartości są następujące:<br /><br /> - RC4Stream<br />- AES<br /><br /> Wartością domyślną jest RC4Stream. Ten atrybut jest <xref:System.ServiceModel.MsmqEncryptionAlgorithm>typu .|  
|`msmqProtectionLevel`|Określa sposób zabezpieczenia wiadomości na poziomie transportu usługi MSMQ. Szyfrowanie zapewnia integralność wiadomości, podczas gdy EncryptAndSign zapewnia integralność wiadomości i nie odrzuca; oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca jest tym, kim mówią, że są.<br /><br /> - Prawidłowe wartości są następujące:<br />- Brak: Brak ochrony.<br />- Podpisz: Wiadomości są podpisane.<br />- EncryptAndSign: Wiadomości są szyfrowane i podpisane.<br /><br /> Wartością domyślną jest Sign. Ten atrybut jest typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|- Określa algorytm, który ma być używany do obliczania skrótu jako część podpisów. Prawidłowe wartości są następujące:<br />- MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> Wartością domyślną jest SHA1. Ten atrybut jest <xref:System.ServiceModel.MsmqSecureHashAlgorithm>typu .<br>Ze względu na problemy z kolizją z MD5 i SHA1 firma Microsoft zaleca sha256 lub lepsze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>bezpieczeństwa](security-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element hermetyzuje ustawienia zabezpieczeń dla transportu integracji Usługi kolejkowania wiadomości. Ustawienia są takie same zarówno dla integracji usługi kolejkowania wiadomości, jak i transportów w kolejce. Umożliwia ustawienie trybu uwierzytelniania, algorytmu szyfrowania, bezpiecznego algorytmu mieszania i poziomu ochrony.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<wiążące>](bindings.md)
