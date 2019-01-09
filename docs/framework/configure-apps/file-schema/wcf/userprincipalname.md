---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: ff38a6975d1ec73c1a3014b94198ba630c3fec31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149983"
---
# <a name="ltuserprincipalnamegt"></a>&lt;userPrincipalName&gt;
Określa główną nazwę użytkownika (UPN) usługi uwierzytelniania przez klienta.  
  
 Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<tożsamość >  
\<userPrincipalName>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Nazwa konta użytkownika (czasami określane jako nazwa loginu użytkownika) i nazwa domeny identyfikującej domenę, w którym znajduje się konto użytkownika. Jest to standardowy używana do logowania do domeny Windows. Format to: someone@example.com (podobnie jak adres e-mail).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości używa nazwy UPN, podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji określa nazwy UPN usługi, aby zostać uwierzytelnionym przez klienta.  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
