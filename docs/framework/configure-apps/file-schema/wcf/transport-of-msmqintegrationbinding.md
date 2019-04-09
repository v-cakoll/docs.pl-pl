---
title: <transport> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 3126618eca6e8317968c6eb568a04615ec8de884
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073458"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<transport> of \<msmqIntegrationBinding>
Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.  
  
 \<system.ServiceModel>  
\<powiązania >  
msmqIntegrationBinding  
\<Powiązanie >  
\<security>  
\<transport>  
  
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
|`msmqAuthenticationMode`|Określa, jak wiadomość musi zostać uwierzytelniony przez usługę transportową MSMQ. Jeśli jest ono ustawione na `None`, wartość `msmqProtectionLevel` atrybut również musi być ustawiona na `None`.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -Brak: Bez uwierzytelniania.<br />-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory, aby uzyskać certyfikat X.509, identyfikator SID skojarzone z wiadomością. Następnie służy do Sprawdź, czy lista ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu do kolejki.<br />-Certyfikat: Kanał uzyskuje certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to WindowsDomain. Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Określa algorytm używany do szyfrowania wiadomości na łączu podczas transferu wiadomości między menedżerami kolejki wiadomości. Prawidłowe wartości są następujące:<br /><br /> -RC4Stream<br />-AES<br /><br /> Wartość domyślna to RC4Stream. Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Określa, w jaki sposób wiadomość jest zabezpieczona na poziomie usługi transportu MSMQ. Szyfrowanie zapewnia integralność wiadomości, podczas gdy EncryptAndSign zapewnia integralność komunikatów i uznawania; oznacza to w rzeczywistości pochodzą od nadawcy i informacje o nadawcy mają który mówi, że jest on.<br /><br /> -Prawidłowe wartości są następujące:<br />-Brak: Brak ochrony.<br />— Logowanie: Komunikaty są podpisane.<br />-EncryptAndSign: Komunikaty są szyfrowane i podpisany.<br /><br /> Wartość domyślna to znak. Ten atrybut jest typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|-Określa algorytm, który ma być używany w obliczeniu skrótu jako części podpisów. Prawidłowe wartości są następujące:<br />-   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Wartość domyślna to SHA1. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Z powodu problemów kolizji z MD5 lub SHA1 firma Microsoft zaleca SHA256 lub lepszej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązanie usługi MSMQ.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element hermetyzuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów. Ustawienia są takie same, Integracja usługi kolejkowania komunikatów i umieszczonych w kolejce transportów. Umożliwia ustawienie Tryb uwierzytelniania, algorytmów szyfrowania, Secure Hash Algorithm i poziom ochrony.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą wiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
