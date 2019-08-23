---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940532"
---
# <a name="usernameauthentication"></a><span data-ttu-id="9ed55-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="9ed55-101">\<userNameAuthentication></span></span>
<span data-ttu-id="9ed55-102">Określa poświadczenia usługi na podstawie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="9ed55-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="9ed55-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9ed55-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9ed55-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="9ed55-104">\<behaviors></span></span>  
<span data-ttu-id="9ed55-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9ed55-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9ed55-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="9ed55-106">\<behavior></span></span>  
<span data-ttu-id="9ed55-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9ed55-107">\<serviceCredentials></span></span>  
<span data-ttu-id="9ed55-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="9ed55-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed55-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ed55-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ed55-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ed55-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ed55-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ed55-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ed55-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ed55-112">Attributes</span></span>  
  
|<span data-ttu-id="9ed55-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9ed55-113">Attribute</span></span>|<span data-ttu-id="9ed55-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed55-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="9ed55-115">A <xref:System.TimeSpan> , która określa maksymalny czas buforowania tokenu.</span><span class="sxs-lookup"><span data-stu-id="9ed55-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="9ed55-116">Wartość domyślna to 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="9ed55-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="9ed55-117">Wartość logiczna określająca, czy tokeny logowania są buforowane.</span><span class="sxs-lookup"><span data-stu-id="9ed55-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="9ed55-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9ed55-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="9ed55-119">Ciąg określający typ niestandardowego modułu weryfikacji hasła użytkownika, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9ed55-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="9ed55-120">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9ed55-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="9ed55-121">Wartość logiczna określająca, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9ed55-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="9ed55-122">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9ed55-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="9ed55-123">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ skutkuje rozwinięciem całej grupy.</span><span class="sxs-lookup"><span data-stu-id="9ed55-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="9ed55-124">Ustaw tę właściwość na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="9ed55-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="9ed55-125">Liczba całkowita określająca maksymalną liczbę tokenów logowania do buforowania.</span><span class="sxs-lookup"><span data-stu-id="9ed55-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="9ed55-126">Ta wartość powinna być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="9ed55-126">This value should be larger than zero.</span></span> <span data-ttu-id="9ed55-127">Wartość domyślna to 128.</span><span class="sxs-lookup"><span data-stu-id="9ed55-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="9ed55-128">Gdy atrybut powiązania jest ustawiony na `username`, nazwa użytkownika jest mapowana na konta systemu Windows. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="9ed55-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="9ed55-129">Można przesłonić to zachowanie przy użyciu tego atrybutu, który jest ciągiem zawierającym nazwę <xref:System.Web.Security.MembershipProvider> wartości, która zapewnia odpowiedni mechanizm walidacji hasła.</span><span class="sxs-lookup"><span data-stu-id="9ed55-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="9ed55-130">Określa sposób sprawdzania poprawności hasła nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ed55-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="9ed55-131">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9ed55-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="9ed55-132">— System Windows</span><span class="sxs-lookup"><span data-stu-id="9ed55-132">-   Windows</span></span><br /><span data-ttu-id="9ed55-133">- MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="9ed55-133">-   MembershipProvider</span></span><br /><span data-ttu-id="9ed55-134">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9ed55-134">-   Custom</span></span><br /><br /> <span data-ttu-id="9ed55-135">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="9ed55-135">The default is Windows.</span></span> <span data-ttu-id="9ed55-136">Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="9ed55-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ed55-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ed55-137">Child Elements</span></span>  
 <span data-ttu-id="9ed55-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ed55-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ed55-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ed55-139">Parent Elements</span></span>  
  
|<span data-ttu-id="9ed55-140">Element</span><span class="sxs-lookup"><span data-stu-id="9ed55-140">Element</span></span>|<span data-ttu-id="9ed55-141">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed55-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ed55-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9ed55-142">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="9ed55-143">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi oraz ustawienia powiązane z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="9ed55-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed55-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ed55-144">Remarks</span></span>  
 <span data-ttu-id="9ed55-145">Jeśli żaden z powiązań używanych przez usługę nie jest skonfigurowany do uwierzytelniania opartego na nazwie użytkownika/hasła, atrybuty tego elementu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9ed55-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="9ed55-146">Należą `customUserNamePasswordValidatorType`do nich `includeWindowsGroups`, `membershipProviderName`,, `userNamePasswordValidationMode`i.</span><span class="sxs-lookup"><span data-stu-id="9ed55-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="9ed55-147">Jeśli żaden z powiązań używanych przez usługę nie jest skonfigurowany do korzystania z uwierzytelniania systemu Windows dla nazwy użytkownika/hasła, ustawienia związane z buforowaniem tokenów logowania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9ed55-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="9ed55-148">Należą do `cacheLogonTokenLifetime`nich, `cacheLogonTokens`i. `maxCacheLogonTokens`</span><span class="sxs-lookup"><span data-stu-id="9ed55-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed55-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ed55-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
