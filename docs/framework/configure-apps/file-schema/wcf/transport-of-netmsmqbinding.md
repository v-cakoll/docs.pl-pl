---
title: '&lt;transport&gt; w &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 611d6730695c2e353782d11cb74d391107c02c35
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
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
|msmqAuthenticationMode|Określa jak wiadomość musi być uwierzytelniani przez usługę transportową MSMQ. Prawidłowe wartości są następujące:<br /><br /> -Brak: Bez uwierzytelniania.<br />-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory można pobrać certyfikatu X.509 identyfikator zabezpieczeń skojarzony z komunikatem. Służy to następnie sprawdź, czy listy ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu dla kolejki.<br />-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.<br /><br /> Wartość domyślna to `WindowsDomain`.<br /><br /> Jeśli ten atrybut ma ustawioną `None`, `msmqProtectionLevel` atrybutu również musi być ustawiona na `None`. Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Określa algorytm używany do szyfrowania wiadomości w sieci podczas transferu wiadomości między menedżerami kolejki wiadomości. Prawidłowe wartości są następujące:<br /><br /> -   RC4Stream<br />-AES<br />— Wartość domyślna to `RC4Stream`. Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Określa sposób wiadomości są zabezpieczone na poziomie usługi transportu MSMQ. Szyfrowanie gwarantuje, że komunikat integralności, podczas logowania i szyfrowania zapewnia zarówno integralność komunikatów i wyłączność podpisu. To, że wiadomość rzeczywiście pochodzi od nadawcy i jest nadawcy, który mówi się, że jest on. Prawidłowe wartości są następujące:<br /><br /> -Brak: Brak ochrony.<br />-Znak: Komunikaty są podpisane.<br />-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.<br />— Wartość domyślna to `Sign`.|  
|msmqSecureHashAlgorithm|Określa algorytm wyznaczania wartości skrótu używanego do obliczania skrót wiadomości. Prawidłowe wartości są następujące:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Wartość domyślna to `SHA1`. Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń transportu dla transportów umieszczonych w kolejce.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
