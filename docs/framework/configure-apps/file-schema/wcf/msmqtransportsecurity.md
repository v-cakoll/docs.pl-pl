---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153012"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Określa ustawienia zabezpieczeń transportu usługi MSMQ dla powiązania niestandardowego.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>niestandardowe**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegracja>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Określa sposób uwierzytelniania wiadomości przez transport usługi MSMQ. Jeśli jest ustawiona na `None`wartość `msmqProtectionLevel` , wartość atrybutu `None`musi być również ustawiona na .<br /><br /> Prawidłowe wartości są następujące:<br /><br /> - Brak: Brak uwierzytelniania.<br />- Windows: Mechanizm uwierzytelniania używa usługi Active Directory, aby uzyskać certyfikat X.509 dla identyfikatora SID skojarzonego z wiadomością. Jest to następnie używane do sprawdzania listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu w kolejce.<br />- Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartością domyślną jest system Windows. Ten atrybut jest <xref:System.ServiceModel.MsmqAuthenticationMode>typu .|  
|`msmqEncryptionAlgorithm`|Określa algorytm, który ma być używany do szyfrowania wiadomości w sieci podczas przesyłania wiadomości między menedżerami kolejek komunikatów. Prawidłowe wartości są następujące:<br /><br /> - RC4Stream<br />- AES<br /><br /> Wartością domyślną jest RC4Stream. Ten atrybut jest <xref:System.ServiceModel.MsmqEncryptionAlgorithm>typu .|  
|`msmqProtectionLevel`|Określa sposób zabezpieczenia wiadomości na poziomie transportu usługi MSMQ. Szyfrowanie zapewnia integralność wiadomości, podczas gdy EncryptAndSign zapewnia integralność wiadomości i nie odrzuca; oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca jest tym, kim mówią, że są. Prawidłowe wartości są następujące:<br /><br /> - Brak: Brak ochrony.<br />- Podpisz: Wiadomości są podpisane.<br />- EncryptAndSign: Wiadomości są szyfrowane i podpisane.<br /><br /> Wartością domyślną jest Sign. Ten atrybut jest <xref:System.Net.Security.ProtectionLevel>typu .|  
|`msmqSecureHashAlgorithm`|Określa algorytm, który ma być używany do obliczania skrótu jako część podpisów. Prawidłowe wartości są następujące:<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> Wartością domyślną jest SHA1. Ten atrybut jest <xref:System.ServiceModel.MsmqSecureHashAlgorithm>typu .<br>Ze względu na problemy z kolizją z MD5 i SHA1 firma Microsoft zaleca sha256 lub lepsze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<msmqIntegracja>](msmqintegration.md)|Określa ustawienia wymagane do interakcji z nadawcą lub odbiorcą usługi kolejkowania wiadomości (MSMQ).|  
|[\<>msmqTransport](msmqtransport.md)|Określa właściwości komunikacji kolejkowania dla usługi Windows Communication Foundation (WCF), która używa macierzystego protokołu MSMQ.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat zabezpieczeń transportu, zobacz [Bezpieczeństwo transportu](../../../wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<>niestandardowe](custombinding.md)
- [Zabezpieczenia transportu](../../../wcf/feature-details/transport-security.md)
