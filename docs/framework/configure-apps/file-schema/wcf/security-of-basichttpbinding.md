---
title: '&lt;security&gt; w &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2adb5736cca59d42ab3c62d61513bbfd80a4be04
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45589407"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a>&lt;security&gt; w &lt;basicHttpBinding&gt;
Definiuje możliwości zabezpieczeń [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<basicHttpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalna. Określa typ zabezpieczeń, która jest używana. Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|— Liczba komunikatów nie są zabezpieczane podczas przesyłania.|  
|Transportu|Zabezpieczenia za pomocą transportu HTTPS. Komunikaty protokołu SOAP są chronione przy użyciu protokołu HTTPS. Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi. Klient jest uwierzytelniany przy użyciu właściwości ClientCredentialType o wartości dostarczone. Zobacz [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|Komunikat|Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP. Domyślnie treść jest zaszyfrowany i podpisany. Dla tego powiązania systemu wymaga podania certyfikatu serwera do klienta poza pasmem. Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.|  
|TransportWithMessageCredential|Uwierzytelnianie integralności, poufności i serwera są dostarczane przez zabezpieczeń transportu. Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP. Ten tryb jest istotne, po użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.|  
|TransportCredentialOnly|Ten tryb nie zapewnia integralność komunikatów i poufność. Zapewnia uwierzytelnianie oparte na protokole http klienta. W tym trybie, należy używać ostrożnie. Należy używać w środowiskach, gdzie zabezpieczenia transportu jest świadczona w inny sposób (takich jak IPSec), a tylko uwierzytelnianie klientów jest świadczona przez infrastrukturę usługi WCF.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Określa ustawienia zabezpieczenia transportu podstawowa usługa HTTP. Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP. Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony. Ten element umożliwia konfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
