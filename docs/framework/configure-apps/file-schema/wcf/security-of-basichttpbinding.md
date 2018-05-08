---
title: '&lt;security&gt; w &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e39d32a9cc689905bed42f56e4f998bbd8c6e038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a>&lt;security&gt; w &lt;basicHttpBinding&gt;
Możliwości zabezpieczeń definiuje [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
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
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Opcjonalna. Określa typ zabezpieczeń, który jest używany. Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|— Liczba komunikatów nie są już zabezpieczone podczas transferu.|  
|Transportu|Zabezpieczenia transportu HTTPS. Wiadomości SOAP są chronione przy użyciu protokołu HTTPS. Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi. Klient jest uwierzytelniany przy użyciu ClientCredentialType dostarczony. Zobacz [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|Komunikat|Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP. Domyślnie treści zostaje zaszyfrowany i podpisany. Dla tego powiązania system wymaga podania certyfikatu serwera do klienta poza pasmem. Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.|  
|TransportWithMessageCredential|Uwierzytelnianie integralności i poufności serwera są udostępniane za pośrednictwem zabezpieczeń transportu. Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP. Ten tryb jest istotne, gdy uwierzytelnia użytkownika przy użyciu nazwy użytkownika i hasła i ma istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.|  
|TransportCredentialOnly|W tym trybie nie zapewnia integralności i poufności. Zapewnia uwierzytelnianie oparte na protokole http klienta. Tego trybu należy używać ostrożnie. Można stosować w środowiskach, gdzie zabezpieczeń transportu jest świadczona w inny sposób (na przykład IPSec), a tylko uwierzytelnianie klienta jest zapewniana przez infrastrukturę programu WCF.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń transportu podstawowa usługa HTTP. Ten element odpowiada <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP. Ten element odpowiada <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie komunikatu protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony. Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `basicHttpBinding` elementu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
