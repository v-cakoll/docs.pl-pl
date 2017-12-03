---
title: '&lt;serviceAuthorization&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc04552b9b2ecd85a520ed16ae9a6ee0dfc98a46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthorizationgt-element"></a>&lt;serviceAuthorization&gt;, element
Określa ustawienia, które zezwalają na dostęp do operacji usługi  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceAuthorization >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|ImpersonateCallerForAllOperations|Wartość logiczna określająca, czy wszystkie operacje usługi personifikują wywołującego. Wartość domyślna to `false`.<br /><br /> Określonej operacji usługi personifikuje wywołującego, kontekst wątku jest włączane w kontekście wywołującego przed wykonaniem określonej usługi.|  
|principalPermissionMode|Ustawia zabezpieczenie używane do wykonywania operacji na serwerze. Następujące wartości:<br /><br /> -Brak<br />-UseWindowsGroups<br />-UseAspNetRoles<br />-Niestandardowe<br /><br /> Wartość domyślna to UseWindowsGroups. Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz [porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Ciąg określający nazwę dostawcy ról, który zawiera informacje o rolach dla aplikacji Windows Communication Foundation (WCF). Wartość domyślna to ciąg pusty.|  
|ServiceAuthorizationManagerType|Ciąg zawierający typ Menedżera usług autoryzacji. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|authorizationPolicies|Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` — słowo kluczowe. Każdej zasady autoryzacji zawiera jeden z wymaganych `policyType` atrybut, który jest ciągiem. Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń. Udzielono lub odmówiono kontrola dostępu oparta na. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Zawiera kolekcję ustawień zachowania dla usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera elementy mające wpływ na autoryzacji, dostawców niestandardowej roli zabezpieczeń i personifikacji.  
  
 `principalPermissionMode` Atrybut określa grupy użytkowników do użycia podczas nadanie Metoda chroniona. Wartość domyślna to `UseWindowsGroups` i określa, czy grupy systemu Windows, takich jak "Administratorzy" lub "Użytkownicy", przeszukiwane są próby uzyskania dostępu do zasobu tożsamości. Można również określić `UseAspNetRoles` do korzystania z dostawcy niestandardowej roli zabezpieczeń, który jest skonfigurowany pod \<system.web > element, jak pokazano w poniższym kodzie.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Poniższy kod przedstawia `roleProviderName` używane z `principalPermissionMode` atrybutu.  
  
```xml  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 Aby uzyskać szczegółowy przykład za pomocą tego elementu konfiguracji, zobacz [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md)
