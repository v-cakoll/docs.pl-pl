---
title: '&lt;RSA&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 8005fd67b92cb14d82b525e7c990f9d58aef7b58
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145344"
---
# <a name="ltrsagt"></a>&lt;RSA&gt;
Bezpieczny klient WCF łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia, który zawiera klucz publiczny RSA użyta do skonstruowania tej tożsamości.  
  
 \<tożsamość >  
\<RSA >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Opcjonalny ciąg. Wartość klucza publicznego RSA porównana z na komputerze klienckim.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Sprawdzanie RSA umożliwia takie ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA lub wygenerowane swoją własną wartością klucza RSA. Ten umożliwia bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi nie jest już współpracuje z istniejącymi klientami, zmiana wartości klucza RSA.  
  
 Aby uzyskać więcej informacji o weryfikacji usługi do klienta za pomocą tożsamości, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X.509, który jest używany do uwierzytelniania serwera.  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
