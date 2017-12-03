---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 616eb07a76da93ff1019ea7e80b5ce3151e6e8a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserprincipalnamegt"></a>&lt;userPrincipalName&gt;
Określa główną nazwę użytkownika (UPN) usługi uwierzytelniania przez klienta.  
  
 Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<tożsamość >  
\<userPrincipalName >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Nazwa konta użytkownika (czasem określana jako nazwa logowania użytkownika) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika. Jest to standardowy używana do logowania do domeny systemu Windows. Format: someone@example.com (podobnie jak w przypadku adresu e-mail).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość usługi uwierzytelniania przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klient łączący punkt końcowy o tej tożsamości używa nazwy UPN, gdy z punktem końcowym uwierzytelniania SSPI.  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji określa nazwę UPN usługi uwierzytelniania przez klienta.  
  
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
