---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 5d65b5956491e30066ece54a48374f1d7014552e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657607"
---
# <a name="ltserviceprincipalnamegt"></a>&lt;servicePrincipalName&gt;
Określa tożsamość usługi przez jego głównej nazwy usługi (SPN).  
  
 Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<identity>  
\<servicePrincipalName>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi. Jeśli zainstalowano wiele wystąpień usługi na komputerach w całym lesie, każde wystąpienie musi mieć własną nazwę SPN. Wystąpienie danej usługi może mieć wiele nazw SPN, jeśli istnieje kilka nazw, które klienci mogą korzystać z uwierzytelniania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości używa nazwy SPN podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
