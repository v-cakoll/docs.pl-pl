---
title: '&lt;serviceAuthorization&gt;, element'
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: 6c69d10eb2f6cdf4546dd5895d196723417f5494
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146007"
---
# <a name="ltserviceauthorizationgt-element"></a><span data-ttu-id="5ca39-102">&lt;serviceAuthorization&gt;, element</span><span class="sxs-lookup"><span data-stu-id="5ca39-102">&lt;serviceAuthorization&gt; element</span></span>
<span data-ttu-id="5ca39-103">Określa ustawienia, które zezwalają na dostęp do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="5ca39-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="5ca39-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ca39-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ca39-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="5ca39-105">\<behaviors></span></span>  
<span data-ttu-id="5ca39-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5ca39-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5ca39-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5ca39-107">\<behavior></span></span>  
<span data-ttu-id="5ca39-108">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="5ca39-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca39-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ca39-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca39-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5ca39-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ca39-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5ca39-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca39-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ca39-112">Attributes</span></span>  
  
|<span data-ttu-id="5ca39-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ca39-113">Attribute</span></span>|<span data-ttu-id="5ca39-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5ca39-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ca39-115">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="5ca39-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="5ca39-116">Wartość logiczna określająca, jeśli wszystkie operacje usługi personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5ca39-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="5ca39-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5ca39-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="5ca39-118">Kiedy określonej operacji usługi personifikuje obiekt wywołujący, kontekst wątku jest włączane do kontekstu obiekt wywołujący przed wykonaniem określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="5ca39-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="5ca39-119">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="5ca39-119">principalPermissionMode</span></span>|<span data-ttu-id="5ca39-120">Ustawia zabezpieczenie używane do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="5ca39-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="5ca39-121">Następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="5ca39-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="5ca39-122">-Brak</span><span class="sxs-lookup"><span data-stu-id="5ca39-122">-   None</span></span><br /><span data-ttu-id="5ca39-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="5ca39-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="5ca39-124">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="5ca39-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="5ca39-125">— Niestandardowa</span><span class="sxs-lookup"><span data-stu-id="5ca39-125">-   Custom</span></span><br /><br /> <span data-ttu-id="5ca39-126">Wartość domyślna to UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="5ca39-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="5ca39-127">Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="5ca39-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="5ca39-128">Aby uzyskać więcej informacji na temat korzystania z tego atrybutu, zobacz [jak: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="5ca39-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="5ca39-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="5ca39-129">roleProviderName</span></span>|<span data-ttu-id="5ca39-130">Ciąg, który określa nazwę dostawcy ról, który dostarcza informacje o rolach dla aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5ca39-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5ca39-131">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="5ca39-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="5ca39-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="5ca39-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="5ca39-133">Ciąg zawierający typ Menedżera usług autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="5ca39-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="5ca39-134">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="5ca39-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ca39-135">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5ca39-135">Child Elements</span></span>  
  
|<span data-ttu-id="5ca39-136">Element</span><span class="sxs-lookup"><span data-stu-id="5ca39-136">Element</span></span>|<span data-ttu-id="5ca39-137">Opis</span><span class="sxs-lookup"><span data-stu-id="5ca39-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ca39-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="5ca39-138">authorizationPolicies</span></span>|<span data-ttu-id="5ca39-139">Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5ca39-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="5ca39-140">Zasady autoryzacji, każdy zawiera jeden wymagane `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="5ca39-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="5ca39-141">Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="5ca39-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="5ca39-142">Udzielić lub odmówić kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="5ca39-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="5ca39-143">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="5ca39-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca39-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5ca39-144">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca39-145">Element</span><span class="sxs-lookup"><span data-stu-id="5ca39-145">Element</span></span>|<span data-ttu-id="5ca39-146">Opis</span><span class="sxs-lookup"><span data-stu-id="5ca39-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ca39-147">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5ca39-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5ca39-148">Zawiera kolekcję ustawień zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5ca39-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca39-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ca39-149">Remarks</span></span>  
 <span data-ttu-id="5ca39-150">Ta sekcja zawiera elementy wpływające na autoryzacji, ról niestandardowych dostawców i personifikacji.</span><span class="sxs-lookup"><span data-stu-id="5ca39-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="5ca39-151">`principalPermissionMode` Atrybut określa grupy użytkowników do użycia podczas nadanie Metoda chroniona.</span><span class="sxs-lookup"><span data-stu-id="5ca39-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="5ca39-152">Wartość domyślna to `UseWindowsGroups` i określa, czy grupy Windows, takie jak "Administratorzy" lub "Użytkowników", są przeszukiwane pod kątem tożsamości próby uzyskania dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="5ca39-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="5ca39-153">Można również określić `UseAspNetRoles` Używanie dostawcy roli niestandardowej, skonfigurowanym w ramach \<system.web > elementu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5ca39-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="5ca39-154">Poniższy kod przedstawia `roleProviderName` używane z `principalPermissionMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5ca39-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="5ca39-155">Aby uzyskać szczegółowy przykład przy użyciu tego elementu konfiguracji, zobacz [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="5ca39-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca39-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ca39-156">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [<span data-ttu-id="5ca39-157">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5ca39-157">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5ca39-158">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="5ca39-158">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="5ca39-159">Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="5ca39-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="5ca39-160">Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="5ca39-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [<span data-ttu-id="5ca39-161">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="5ca39-161">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
