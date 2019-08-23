---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5a7dcac4edce75029bb2e0293461557f56e3c3be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933221"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Określa ustawienia zabezpieczeń transportu usługi MSMQ dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<msmqIntegration>  
\<msmqTransportSecurity>  
  
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
|`msmqAuthenticationMode`|Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ. Jeśli jest ustawiona na `None`, wartość `msmqProtectionLevel` atrybutu musi również być ustawiona na `None`.<br /><br /> Prawidłowe wartości to:<br /><br /> Dawaj Brak uwierzytelniania.<br />Systemy Mechanizm uwierzytelniania używa Active Directory, aby uzyskać certyfikat X. 509 dla identyfikatora SID skojarzonego z wiadomością. Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu w kolejce.<br />Certyfikatu Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to Windows. Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości. Prawidłowe wartości to:<br /><br /> - RC4Stream<br />-AES<br /><br /> Wartość domyślna to RC4Stream. Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Określa, w jaki sposób wiadomość jest zabezpieczona na poziomie transportu usługi MSMQ. Szyfrowanie zapewnia integralność komunikatów, podczas gdy EncryptAndSign zapewnia integralność komunikatów i odrzucanie. oznacza to, że komunikat rzeczywiście pochodzi od nadawcy, a nadawca jest jego informacją. Prawidłowe wartości to:<br /><br /> Dawaj Brak ochrony.<br />Zapis Komunikaty są podpisane.<br />EncryptAndSign Komunikaty są szyfrowane i podpisane.<br /><br /> Wartość domyślna to Sign. Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.|  
|`msmqSecureHashAlgorithm`|Określa algorytm, który ma być używany podczas obliczania skrótu jako części podpisów. Prawidłowe wartości to:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Wartość domyślna to SHA1. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|Określa ustawienia wymagane do interakcji z nadawcą lub odbiornikiem usługi kolejkowania komunikatów (MSMQ).|  
|[\<msmqTransport>](msmqtransport.md)|Określa właściwości komunikacji kolejkowania dla usługi Windows Communication Foundation (WCF), która używa natywnego protokołu MSMQ.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat zabezpieczeń transportu, zobacz [Transport Security](../../../wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Zabezpieczenia transportu](../../../wcf/feature-details/transport-security.md)
