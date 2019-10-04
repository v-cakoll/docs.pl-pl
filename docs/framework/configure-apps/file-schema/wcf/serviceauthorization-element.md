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
# <a name="serviceauthorization-element"></a><span data-ttu-id="f6a48-102">\<serviceAuthorization > elementu</span><span class="sxs-lookup"><span data-stu-id="f6a48-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="f6a48-103">Określa ustawienia, które autoryzują dostęp do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="f6a48-103">Specifies settings that authorize access to service operations</span></span>

<span data-ttu-id="f6a48-104">[ **\<configuration >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6a48-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f6a48-105">&nbsp; @ no__t-1[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f6a48-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f6a48-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<behaviors >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f6a48-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f6a48-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f6a48-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="f6a48-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0behavior >** ](behavior-of-servicebehaviors.md)1</span><span class="sxs-lookup"><span data-stu-id="f6a48-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\</span></span>
<span data-ttu-id="f6a48-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="f6a48-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="f6a48-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6a48-110">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="f6a48-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6a48-111">Attributes and elements</span></span>

<span data-ttu-id="f6a48-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne:</span><span class="sxs-lookup"><span data-stu-id="f6a48-112">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="f6a48-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6a48-113">Attributes</span></span>

|<span data-ttu-id="f6a48-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6a48-114">Attribute</span></span>|<span data-ttu-id="f6a48-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f6a48-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6a48-116">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="f6a48-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="f6a48-117">Wartość logiczna określająca, czy wszystkie operacje w usłudze personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f6a48-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="f6a48-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f6a48-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f6a48-119">Gdy określona operacja usługi personifikuje obiekt wywołujący, kontekst wątku jest przełączany do kontekstu wywołującego przed wykonaniem określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="f6a48-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="f6a48-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="f6a48-120">principalPermissionMode</span></span>|<span data-ttu-id="f6a48-121">Ustawia podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f6a48-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="f6a48-122">Dostępne są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="f6a48-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="f6a48-123">-Brak</span><span class="sxs-lookup"><span data-stu-id="f6a48-123">-   None</span></span><br /><span data-ttu-id="f6a48-124">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="f6a48-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="f6a48-125">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="f6a48-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="f6a48-126">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f6a48-126">-   Custom</span></span><br /><br /> <span data-ttu-id="f6a48-127">Wartość domyślna to UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="f6a48-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="f6a48-128">Wartość jest typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="f6a48-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="f6a48-129">Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz [How to: ograniczanie dostępu za pomocą klasy PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="f6a48-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="f6a48-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="f6a48-130">roleProviderName</span></span>|<span data-ttu-id="f6a48-131">Ciąg określający nazwę dostawcy ról, który dostarcza informacje o roli dla aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f6a48-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f6a48-132">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="f6a48-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="f6a48-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="f6a48-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="f6a48-134">Ciąg zawierający typ Menedżera autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f6a48-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="f6a48-135">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="f6a48-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="f6a48-136">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6a48-136">Child elements</span></span>

|<span data-ttu-id="f6a48-137">Element</span><span class="sxs-lookup"><span data-stu-id="f6a48-137">Element</span></span>|<span data-ttu-id="f6a48-138">Opis</span><span class="sxs-lookup"><span data-stu-id="f6a48-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6a48-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="f6a48-139">authorizationPolicies</span></span>|<span data-ttu-id="f6a48-140">Zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą słowa kluczowego `add`.</span><span class="sxs-lookup"><span data-stu-id="f6a48-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="f6a48-141">Każda zasada autoryzacji zawiera jeden wymagany atrybut `policyType`, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="f6a48-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="f6a48-142">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="f6a48-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="f6a48-143">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="f6a48-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="f6a48-144">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="f6a48-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="f6a48-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6a48-145">Parent elements</span></span>

|<span data-ttu-id="f6a48-146">Element</span><span class="sxs-lookup"><span data-stu-id="f6a48-146">Element</span></span>|<span data-ttu-id="f6a48-147">Opis</span><span class="sxs-lookup"><span data-stu-id="f6a48-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6a48-148">@no__t — 1behavior ></span><span class="sxs-lookup"><span data-stu-id="f6a48-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f6a48-149">Zawiera kolekcję ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="f6a48-149">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="f6a48-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6a48-150">Remarks</span></span>

<span data-ttu-id="f6a48-151">Ta sekcja zawiera elementy wpływające na autoryzację, niestandardowych dostawców ról i personifikacji.</span><span class="sxs-lookup"><span data-stu-id="f6a48-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="f6a48-152">Atrybut `principalPermissionMode` określa grupy użytkowników do użycia podczas autoryzowania używania metody chronionej.</span><span class="sxs-lookup"><span data-stu-id="f6a48-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="f6a48-153">Wartość domyślna to `UseWindowsGroups` i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6a48-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="f6a48-154">Możesz również określić `UseAspNetRoles`, aby użyć niestandardowego dostawcy roli, który jest skonfigurowany w ramach elementu @no__t -1System. Web >, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f6a48-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="f6a48-155">Poniższy kod ilustruje `roleProviderName` używany z atrybutem `principalPermissionMode`:</span><span class="sxs-lookup"><span data-stu-id="f6a48-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="f6a48-156">Aby zapoznać się ze szczegółowym przykładem użycia tego elementu konfiguracji, zobacz [autoryzowanie dostępu do operacji usługi](../../../wcf/samples/authorizing-access-to-service-operations.md) i [zasad autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="f6a48-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f6a48-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6a48-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="f6a48-158">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f6a48-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f6a48-159">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="f6a48-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="f6a48-160">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="f6a48-160">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="f6a48-161">Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="f6a48-161">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="f6a48-162">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="f6a48-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
