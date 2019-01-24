---
title: '&lt;transport&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 7eac5c7a0da71e2d06929322ac5c702d83a1ea65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597440"
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a>&lt;transport&gt; w &lt;netMsmqBinding&gt;
Określa ustawienia zabezpieczenia transportu.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netMsmqBinding>  
\<Powiązanie >  
\<security>  
\<transport>  
  
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
|msmqAuthenticationMode|Określa, jak wiadomość musi zostać uwierzytelniony przez usługę transportową MSMQ. Prawidłowe wartości są następujące:<br /><br /> -Brak: Bez uwierzytelniania.<br />-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory można pobrać certyfikatu X.509 dla identyfikatora zabezpieczeń skojarzonych z wiadomością. Następnie służy do Sprawdź, czy lista ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu dla kolejki.<br />-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to `WindowsDomain`.<br /><br /> Jeśli ten atrybut jest ustawiony na `None`, `msmqProtectionLevel` atrybut również musi być ustawiona na `None`. Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Określa algorytm używany do szyfrowania wiadomości na łączu podczas transferu wiadomości między menedżerami kolejki wiadomości. Prawidłowe wartości są następujące:<br /><br /> -RC4Stream<br />-AES<br />— Wartość domyślna to `RC4Stream`. Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Określa, że sposób wiadomości są zabezpieczone na poziomie usługi transportu MSMQ. Szyfrowanie zapewnia, że komunikat integralności, podczas logowania i szyfrowania zapewnia integralność komunikatów i uznawania. Oznacza to komunikat w rzeczywistości pochodzi od nadawcy i informacje o nadawcy mają który mówi, że jest on. Prawidłowe wartości są następujące:<br /><br /> -Brak: Brak ochrony.<br />— Logowanie: Komunikaty są podpisane.<br />-EncryptAndSign: Komunikaty są szyfrowane i podpisany.<br />— Wartość domyślna to `Sign`.|  
|msmqSecureHashAlgorithm|Określa algorytm wyznaczania wartości skrótu, który ma być używany do przetwarzania danych skrót wiadomości. Prawidłowe wartości są następujące:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Wartość domyślna to `SHA1`. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Określa ustawienia zabezpieczenia transportu dla transportów umieszczonych w kolejce.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
