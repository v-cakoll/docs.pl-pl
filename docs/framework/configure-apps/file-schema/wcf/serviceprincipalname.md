---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936154"
---
# <a name="serviceprincipalname"></a>\<servicePrincipalName>
Określa tożsamość usługi za pomocą nazwy głównej usługi (SPN).  
  
 Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
 \<> tożsamości  
\<servicePrincipalName>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi. W przypadku instalowania wielu wystąpień usługi na komputerach w lesie, każde wystąpienie musi mieć własną nazwę SPN. Dana nazwa wystąpienia usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazwy, których klienci mogą używać na potrzeby uwierzytelniania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> tożsamości](identity.md)|Określa tożsamość usługi do uwierzytelnienia przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy SPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [Uwierzytelnianie i tożsamość usług](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<> tożsamości](identity.md)
