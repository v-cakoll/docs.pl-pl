---
title: <serviceAuthorization>, element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834022"
---
# <a name="serviceauthorization-element"></a>Element > \<ServiceAuthorization

Określa ustawienia, które autoryzują dostęp do operacji usługi

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**zachowania\<** ](behaviors.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**serviceBehaviors**](servicebehaviors.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zachowanie**](behavior-of-servicebehaviors.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ServiceAuthorization >**  

## <a name="syntax"></a>Składnia

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne:

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|Wartość logiczna określająca, czy wszystkie operacje w usłudze personifikują wywołującego. Wartość domyślna to `false`.<br /><br /> Gdy określona operacja usługi personifikuje obiekt wywołujący, kontekst wątku jest przełączany do kontekstu wywołującego przed wykonaniem określonej usługi.|  
|principalPermissionMode|Ustawia podmiot zabezpieczeń używany do wykonywania operacji na serwerze. Dostępne są następujące wartości:<br /><br /> -Brak<br />- UseWindowsGroups<br />- UseAspNetRoles<br />-Niestandardowe<br /><br /> Wartość domyślna to UseWindowsGroups. Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz [How to: ograniczanie dostępu za pomocą klasy PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Ciąg określający nazwę dostawcy ról, który dostarcza informacje o roli dla aplikacji Windows Communication Foundation (WCF). Wartość domyślna to pusty ciąg.|  
|ServiceAuthorizationManagerType|Ciąg zawierający typ Menedżera autoryzacji usługi. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.|  

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|  
|-------------|-----------------|  
|authorizationPolicies|Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą słowa kluczowego `add`. Każda zasada autoryzacji zawiera jeden wymagany atrybut `policyType`, który jest ciągiem. Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń. Na podstawie tego można udzielić lub odmówić kontroli dostępu. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|  
|-------------|-----------------|  
|[zachowanie \<>](behavior-of-endpointbehaviors.md)|Zawiera kolekcję ustawień zachowania usługi.|  

## <a name="remarks"></a>Uwagi

Ta sekcja zawiera elementy wpływające na autoryzację, niestandardowych dostawców ról i personifikacji.  
  
Atrybut `principalPermissionMode` określa grupy użytkowników do użycia podczas autoryzowania używania metody chronionej. Wartość domyślna to `UseWindowsGroups` i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu. Możesz również określić `UseAspNetRoles`, aby użyć niestandardowego dostawcy roli, który jest skonfigurowany w ramach elementu \<system. Web >, jak pokazano w poniższym kodzie:

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
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
  <!-- Other configuration code not shown. -->
</system.web>
```
  
Poniższy kod przedstawia `roleProviderName` używany z atrybutem `principalPermissionMode`:
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

Aby zapoznać się ze szczegółowym przykładem użycia tego elementu konfiguracji, zobacz [autoryzowanie dostępu do operacji usługi](../../../wcf/samples/authorizing-access-to-service-operations.md) i [zasad autoryzacji](../../../wcf/samples/authorization-policy.md).
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Autoryzowanie dostępu do operacji usługi](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Zasady autoryzacji](../../../wcf/samples/authorization-policy.md)
