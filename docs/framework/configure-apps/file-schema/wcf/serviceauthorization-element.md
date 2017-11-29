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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cdbe676fa73c040737c947902d64b2c0e689e2a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceauthorizationgt-element"></a><span data-ttu-id="cfd21-102">&lt;serviceAuthorization&gt;, element</span><span class="sxs-lookup"><span data-stu-id="cfd21-102">&lt;serviceAuthorization&gt; element</span></span>
<span data-ttu-id="cfd21-103">Określa ustawienia, które zezwalają na dostęp do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="cfd21-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="cfd21-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cfd21-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfd21-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cfd21-105">\<behaviors></span></span>  
<span data-ttu-id="cfd21-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cfd21-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cfd21-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cfd21-107">\<behavior></span></span>  
<span data-ttu-id="cfd21-108">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="cfd21-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd21-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfd21-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfd21-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cfd21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cfd21-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cfd21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfd21-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cfd21-112">Attributes</span></span>  
  
|<span data-ttu-id="cfd21-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cfd21-113">Attribute</span></span>|<span data-ttu-id="cfd21-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cfd21-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfd21-115">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="cfd21-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="cfd21-116">Wartość logiczna określająca, czy wszystkie operacje usługi personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cfd21-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="cfd21-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="cfd21-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="cfd21-118">Określonej operacji usługi personifikuje wywołującego, kontekst wątku jest włączane w kontekście wywołującego przed wykonaniem określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="cfd21-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="cfd21-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="cfd21-119">principalPermissionMode</span></span>|<span data-ttu-id="cfd21-120">Ustawia zabezpieczenie używane do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="cfd21-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="cfd21-121">Następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="cfd21-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="cfd21-122">-Brak</span><span class="sxs-lookup"><span data-stu-id="cfd21-122">-   None</span></span><br /><span data-ttu-id="cfd21-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="cfd21-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="cfd21-124">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="cfd21-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="cfd21-125">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="cfd21-125">-   Custom</span></span><br /><br /> <span data-ttu-id="cfd21-126">Wartość domyślna to UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="cfd21-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="cfd21-127">Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="cfd21-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="cfd21-128">Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz [porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="cfd21-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="cfd21-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="cfd21-129">roleProviderName</span></span>|<span data-ttu-id="cfd21-130">Ciąg określający nazwę dostawcy ról, który zawiera informacje o rolach dla aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cfd21-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="cfd21-131">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="cfd21-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="cfd21-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="cfd21-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="cfd21-133">Ciąg zawierający typ Menedżera usług autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="cfd21-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="cfd21-134">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="cfd21-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfd21-135">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfd21-135">Child Elements</span></span>  
  
|<span data-ttu-id="cfd21-136">Element</span><span class="sxs-lookup"><span data-stu-id="cfd21-136">Element</span></span>|<span data-ttu-id="cfd21-137">Opis</span><span class="sxs-lookup"><span data-stu-id="cfd21-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfd21-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="cfd21-138">authorizationPolicies</span></span>|<span data-ttu-id="cfd21-139">Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cfd21-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="cfd21-140">Każdej zasady autoryzacji zawiera jeden z wymaganych `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="cfd21-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="cfd21-141">Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="cfd21-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="cfd21-142">Udzielono lub odmówiono kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="cfd21-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="cfd21-143">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="cfd21-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfd21-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfd21-144">Parent Elements</span></span>  
  
|<span data-ttu-id="cfd21-145">Element</span><span class="sxs-lookup"><span data-stu-id="cfd21-145">Element</span></span>|<span data-ttu-id="cfd21-146">Opis</span><span class="sxs-lookup"><span data-stu-id="cfd21-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfd21-147">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cfd21-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cfd21-148">Zawiera kolekcję ustawień zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cfd21-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfd21-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfd21-149">Remarks</span></span>  
 <span data-ttu-id="cfd21-150">Ta sekcja zawiera elementy mające wpływ na autoryzacji, dostawców niestandardowej roli zabezpieczeń i personifikacji.</span><span class="sxs-lookup"><span data-stu-id="cfd21-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="cfd21-151">`principalPermissionMode` Atrybut określa grupy użytkowników do użycia podczas nadanie Metoda chroniona.</span><span class="sxs-lookup"><span data-stu-id="cfd21-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="cfd21-152">Wartość domyślna to `UseWindowsGroups` i określa, czy grupy systemu Windows, takich jak "Administratorzy" lub "Użytkownicy", przeszukiwane są próby uzyskania dostępu do zasobu tożsamości.</span><span class="sxs-lookup"><span data-stu-id="cfd21-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="cfd21-153">Można również określić `UseAspNetRoles` do korzystania z dostawcy niestandardowej roli zabezpieczeń, który jest skonfigurowany pod \<system.web > element, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cfd21-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="cfd21-154">Poniższy kod przedstawia `roleProviderName` używane z `principalPermissionMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cfd21-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 <span data-ttu-id="cfd21-155">Aby uzyskać szczegółowy przykład za pomocą tego elementu konfiguracji, zobacz [Autoryzowanie dostępu do operacji usługi](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="cfd21-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd21-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfd21-156">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [<span data-ttu-id="cfd21-157">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cfd21-157">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cfd21-158">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="cfd21-158">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="cfd21-159">Porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="cfd21-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="cfd21-160">Porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="cfd21-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [<span data-ttu-id="cfd21-161">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="cfd21-161">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
