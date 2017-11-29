---
title: '&lt;transport&gt; w &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9def7fbd0082cc7fa9d9f18388604383cb71f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a>&lt;transport&gt; w &lt;msmqIntegrationBinding&gt;
Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.  
  
 \<System. ServiceModel >  
\<powiązania >  
msmqIntegrationBinding  
\<Powiązanie >  
\<Zabezpieczenia >  
\<transport >  
  
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
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Określa jak wiadomość musi być uwierzytelniani przez usługę transportową MSMQ. Jeśli ta wartość jest równa `None`, wartość `msmqProtectionLevel` atrybutu również musi być ustawiona na `None`.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -Brak: Bez uwierzytelniania.<br />-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory, aby uzyskać certyfikat X.509, identyfikator SID skojarzone z wiadomością. To jest następnie używany do sprawdzania listy ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu w kolejce.<br />-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to WindowsDomain. Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Określa algorytm używany do szyfrowania wiadomości w sieci podczas transferu wiadomości między menedżerami kolejki wiadomości. Prawidłowe wartości są następujące:<br /><br /> -RC4Stream<br />-AES<br /><br /> Wartość domyślna to RC4Stream. Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Określa, jak wiadomość jest zabezpieczona na poziomie transportu MSMQ. Szyfrowanie zapewnia integralność wiadomości, gdy EncryptAndSign zapewnia zarówno integralność komunikatów i bez odrzucania; to, że w rzeczywistości pochodzą od nadawcy i jest nadawcy, który mówi się, że jest on.<br /><br /> -Prawidłowe wartości są następujące:<br />-Brak: Brak ochrony.<br />-Znak: Komunikaty są podpisane.<br />-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.<br /><br /> Wartością domyślną jest znak. Ten atrybut jest typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|— Określa algorytm używany w obliczeniu skrótu jako części podpisów. Prawidłowe wartości są następujące:<br />-MD5<br />-SHA1.<br />-SHA256<br />-SHA512.<br /><br /> Wartość domyślna to SHA1. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element hermetyzuje ustawienia zabezpieczeń dla transport integracji usługi kolejkowania komunikatów. Ustawienia są takie same, Integracja usługi kolejkowania komunikatów i umieszczonych w kolejce transportów. Umożliwia on ustawiony tryb uwierzytelniania, algorytmów szyfrowania, Secure Hash Algorithm i poziom ochrony.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez System](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
