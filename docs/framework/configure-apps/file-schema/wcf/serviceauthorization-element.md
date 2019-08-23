---
title: <serviceAuthorization>, element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b73e2049afb460bf9be8b76ee272ba0547b61453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936397"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="aaa82-102">\<Element > ServiceAuthorization</span><span class="sxs-lookup"><span data-stu-id="aaa82-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="aaa82-103">Określa ustawienia, które autoryzują dostęp do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="aaa82-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="aaa82-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aaa82-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aaa82-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="aaa82-105">\<behaviors></span></span>  
<span data-ttu-id="aaa82-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="aaa82-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="aaa82-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="aaa82-107">\<behavior></span></span>  
<span data-ttu-id="aaa82-108">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="aaa82-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa82-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaa82-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaa82-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aaa82-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aaa82-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aaa82-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaa82-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aaa82-112">Attributes</span></span>  
  
|<span data-ttu-id="aaa82-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aaa82-113">Attribute</span></span>|<span data-ttu-id="aaa82-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa82-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaa82-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="aaa82-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="aaa82-116">Wartość logiczna określająca, czy wszystkie operacje w usłudze personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="aaa82-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="aaa82-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="aaa82-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="aaa82-118">Gdy określona operacja usługi personifikuje obiekt wywołujący, kontekst wątku jest przełączany do kontekstu wywołującego przed wykonaniem określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="aaa82-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="aaa82-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="aaa82-119">principalPermissionMode</span></span>|<span data-ttu-id="aaa82-120">Ustawia podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="aaa82-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="aaa82-121">Dostępne są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="aaa82-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="aaa82-122">-Brak</span><span class="sxs-lookup"><span data-stu-id="aaa82-122">-   None</span></span><br /><span data-ttu-id="aaa82-123">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="aaa82-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="aaa82-124">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="aaa82-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="aaa82-125">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="aaa82-125">-   Custom</span></span><br /><br /> <span data-ttu-id="aaa82-126">Wartość domyślna to UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="aaa82-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="aaa82-127">Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="aaa82-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="aaa82-128">Aby uzyskać więcej informacji na temat używania tego atrybutu [, zobacz How to: Ogranicz dostęp za pomocą klasy](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.</span><span class="sxs-lookup"><span data-stu-id="aaa82-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="aaa82-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="aaa82-129">roleProviderName</span></span>|<span data-ttu-id="aaa82-130">Ciąg określający nazwę dostawcy ról, który dostarcza informacje o roli dla aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="aaa82-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="aaa82-131">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="aaa82-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="aaa82-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="aaa82-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="aaa82-133">Ciąg zawierający typ Menedżera autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="aaa82-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="aaa82-134">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="aaa82-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaa82-135">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aaa82-135">Child Elements</span></span>  
  
|<span data-ttu-id="aaa82-136">Element</span><span class="sxs-lookup"><span data-stu-id="aaa82-136">Element</span></span>|<span data-ttu-id="aaa82-137">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa82-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaa82-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="aaa82-138">authorizationPolicies</span></span>|<span data-ttu-id="aaa82-139">Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="aaa82-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="aaa82-140">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="aaa82-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="aaa82-141">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aaa82-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="aaa82-142">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="aaa82-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="aaa82-143">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="aaa82-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aaa82-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aaa82-144">Parent Elements</span></span>  
  
|<span data-ttu-id="aaa82-145">Element</span><span class="sxs-lookup"><span data-stu-id="aaa82-145">Element</span></span>|<span data-ttu-id="aaa82-146">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa82-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaa82-147">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="aaa82-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="aaa82-148">Zawiera kolekcję ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="aaa82-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa82-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aaa82-149">Remarks</span></span>  
 <span data-ttu-id="aaa82-150">Ta sekcja zawiera elementy wpływające na autoryzację, niestandardowych dostawców ról i personifikacji.</span><span class="sxs-lookup"><span data-stu-id="aaa82-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="aaa82-151">Ten `principalPermissionMode` atrybut określa grupy użytkowników do użycia podczas autoryzowania używania metody chronionej.</span><span class="sxs-lookup"><span data-stu-id="aaa82-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="aaa82-152">Wartość domyślna to `UseWindowsGroups` i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu.</span><span class="sxs-lookup"><span data-stu-id="aaa82-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="aaa82-153">Można również określić `UseAspNetRoles` , aby użyć niestandardowego dostawcy ról, który jest skonfigurowany \<w ramach elementu System. Web >, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="aaa82-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="aaa82-154">Poniższy kod przedstawia `roleProviderName` użycie `principalPermissionMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="aaa82-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="aaa82-155">Aby zapoznać się ze szczegółowym przykładem użycia tego elementu konfiguracji, zobacz [autoryzowanie dostępu do operacji usługi](../../../wcf/samples/authorizing-access-to-service-operations.md) i [zasad autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="aaa82-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa82-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaa82-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="aaa82-157">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="aaa82-157">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="aaa82-158">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="aaa82-158">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="aaa82-159">Instrukcje: Tworzenie niestandardowego Menedżera autoryzacji dla usługi</span><span class="sxs-lookup"><span data-stu-id="aaa82-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="aaa82-160">Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="aaa82-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="aaa82-161">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="aaa82-161">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
