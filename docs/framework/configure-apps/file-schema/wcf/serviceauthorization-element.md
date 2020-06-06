---
title: <serviceAuthorization>, element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834022"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="7d791-102">\<serviceAuthorization>, element</span><span class="sxs-lookup"><span data-stu-id="7d791-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="7d791-103">Określa ustawienia, które autoryzują dostęp do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="7d791-103">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="7d791-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d791-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7d791-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d791-105">Attributes and elements</span></span>

<span data-ttu-id="7d791-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne:</span><span class="sxs-lookup"><span data-stu-id="7d791-106">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="7d791-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d791-107">Attributes</span></span>

|<span data-ttu-id="7d791-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d791-108">Attribute</span></span>|<span data-ttu-id="7d791-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7d791-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d791-110">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="7d791-110">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="7d791-111">Wartość logiczna określająca, czy wszystkie operacje w usłudze personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7d791-111">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="7d791-112">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="7d791-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7d791-113">Gdy określona operacja usługi personifikuje obiekt wywołujący, kontekst wątku jest przełączany do kontekstu wywołującego przed wykonaniem określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="7d791-113">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="7d791-114">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="7d791-114">principalPermissionMode</span></span>|<span data-ttu-id="7d791-115">Ustawia podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7d791-115">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="7d791-116">Dostępne są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="7d791-116">Values include the following:</span></span><br /><br /> <span data-ttu-id="7d791-117">-   Brak</span><span class="sxs-lookup"><span data-stu-id="7d791-117">-   None</span></span><br /><span data-ttu-id="7d791-118">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="7d791-118">-   UseWindowsGroups</span></span><br /><span data-ttu-id="7d791-119">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="7d791-119">-   UseAspNetRoles</span></span><br /><span data-ttu-id="7d791-120">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7d791-120">-   Custom</span></span><br /><br /> <span data-ttu-id="7d791-121">Wartość domyślna to UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="7d791-121">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="7d791-122">Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode> .</span><span class="sxs-lookup"><span data-stu-id="7d791-122">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="7d791-123">Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz [How to: ograniczanie dostępu za pomocą klasy PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="7d791-123">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="7d791-124">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="7d791-124">roleProviderName</span></span>|<span data-ttu-id="7d791-125">Ciąg określający nazwę dostawcy ról, który dostarcza informacje o roli dla aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7d791-125">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="7d791-126">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="7d791-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="7d791-127">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="7d791-127">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="7d791-128">Ciąg zawierający typ Menedżera autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7d791-128">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="7d791-129">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="7d791-129">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="7d791-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d791-130">Child elements</span></span>

|<span data-ttu-id="7d791-131">Element</span><span class="sxs-lookup"><span data-stu-id="7d791-131">Element</span></span>|<span data-ttu-id="7d791-132">Opis</span><span class="sxs-lookup"><span data-stu-id="7d791-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d791-133">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="7d791-133">authorizationPolicies</span></span>|<span data-ttu-id="7d791-134">Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7d791-134">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="7d791-135">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="7d791-135">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="7d791-136">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="7d791-136">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="7d791-137">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="7d791-137">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="7d791-138">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="7d791-138">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="7d791-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d791-139">Parent elements</span></span>

|<span data-ttu-id="7d791-140">Element</span><span class="sxs-lookup"><span data-stu-id="7d791-140">Element</span></span>|<span data-ttu-id="7d791-141">Opis</span><span class="sxs-lookup"><span data-stu-id="7d791-141">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7d791-142">Zawiera kolekcję ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="7d791-142">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="7d791-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d791-143">Remarks</span></span>

<span data-ttu-id="7d791-144">Ta sekcja zawiera elementy wpływające na autoryzację, niestandardowych dostawców ról i personifikacji.</span><span class="sxs-lookup"><span data-stu-id="7d791-144">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="7d791-145">Ten `principalPermissionMode` atrybut określa grupy użytkowników do użycia podczas autoryzowania używania metody chronionej.</span><span class="sxs-lookup"><span data-stu-id="7d791-145">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="7d791-146">Wartość domyślna to `UseWindowsGroups` i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu.</span><span class="sxs-lookup"><span data-stu-id="7d791-146">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="7d791-147">Możesz również określić `UseAspNetRoles` , aby użyć niestandardowego dostawcy ról, który jest skonfigurowany w ramach \<system.web> elementu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="7d791-147">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="7d791-148">Poniższy kod przedstawia `roleProviderName` użyty z `principalPermissionMode` atrybutem:</span><span class="sxs-lookup"><span data-stu-id="7d791-148">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="7d791-149">Aby zapoznać się ze szczegółowym przykładem użycia tego elementu konfiguracji, zobacz [autoryzowanie dostępu do operacji usługi](../../../wcf/samples/authorizing-access-to-service-operations.md) i [zasad autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="7d791-149">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7d791-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d791-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="7d791-151">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d791-151">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7d791-152">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="7d791-152">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="7d791-153">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="7d791-153">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="7d791-154">Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="7d791-154">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="7d791-155">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="7d791-155">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
