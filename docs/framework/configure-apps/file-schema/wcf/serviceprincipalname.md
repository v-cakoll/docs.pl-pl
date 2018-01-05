---
title: '&lt;servicePrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f9b4ec506097cf010af78b3504def08102e0774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceprincipalnamegt"></a>&lt;servicePrincipalName&gt;
Określa tożsamość usługi przez jej nazwy usługi (SPN).  
  
 Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<tożsamość >  
\<servicePrincipalName >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|value|Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi. Jeśli zainstalowano wiele wystąpień usługi na komputerach w całym lesie, każde wystąpienie musi mieć własną nazwę SPN. Wystąpienie danej usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazw, których klienci mogą używać do uwierzytelniania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa tożsamość usługi uwierzytelniania przez klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klient łączący punkt końcowy o tej tożsamości używa główną nazwę usługi, gdy z punktem końcowym uwierzytelniania SSPI.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
