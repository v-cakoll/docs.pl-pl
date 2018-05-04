---
title: '&lt;RSA&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dbeb08e6475d4825ad442b0b264e9003bb6fc53d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltrsagt"></a>&lt;RSA&gt;
Bezpieczny klient WCF łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia, zawierający klucza publicznego RSA użyty do skonstruowania tej tożsamości.  
  
 \<tożsamość >  
\<RSA >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Opcjonalny ciąg. Wartość klucza publicznego RSA ma zostać porównane z na kliencie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość usługi uwierzytelniania przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Sprawdź RSA umożliwia w szczególności ograniczyć uwierzytelnianie oparte na jego klucza RSA jeden certyfikat lub wygenerować własną wartość klucza RSA. Ten umożliwia bardziej restrykcyjne uwierzytelnianie określonego klucza RSA kosztem usługi nie jest już współpracuje z istniejącymi klientami zmiana wartości klucza RSA.  
  
 Aby uzyskać więcej informacji o używaniu tożsamości można sprawdzić poprawności usługi do klienta, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X.509, który jest używany do uwierzytelniania serwera.  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
