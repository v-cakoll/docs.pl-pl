---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399188"
---
# <a name="usernameauthentication"></a><span data-ttu-id="9f06f-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="9f06f-101">\<userNameAuthentication></span></span>
<span data-ttu-id="9f06f-102">Określa poświadczenia usługi na podstawie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="9f06f-102">Specifies a service's credentials based on user name and password.</span></span>  
  
<span data-ttu-id="9f06f-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f06f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f06f-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9f06f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9f06f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9f06f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9f06f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9f06f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9f06f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9f06f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9f06f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9f06f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="9f06f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="9f06f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f06f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f06f-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f06f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9f06f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f06f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9f06f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f06f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f06f-113">Attributes</span></span>  
  
|<span data-ttu-id="9f06f-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9f06f-114">Attribute</span></span>|<span data-ttu-id="9f06f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9f06f-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="9f06f-116">A <xref:System.TimeSpan> , która określa maksymalny czas buforowania tokenu.</span><span class="sxs-lookup"><span data-stu-id="9f06f-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="9f06f-117">Wartość domyślna to 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="9f06f-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="9f06f-118">Wartość logiczna określająca, czy tokeny logowania są buforowane.</span><span class="sxs-lookup"><span data-stu-id="9f06f-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="9f06f-119">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9f06f-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="9f06f-120">Ciąg określający typ niestandardowego modułu weryfikacji hasła użytkownika, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9f06f-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="9f06f-121">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9f06f-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="9f06f-122">Wartość logiczna określająca, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9f06f-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="9f06f-123">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9f06f-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="9f06f-124">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ skutkuje rozwinięciem całej grupy.</span><span class="sxs-lookup"><span data-stu-id="9f06f-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="9f06f-125">Ustaw tę właściwość na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="9f06f-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="9f06f-126">Liczba całkowita określająca maksymalną liczbę tokenów logowania do buforowania.</span><span class="sxs-lookup"><span data-stu-id="9f06f-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="9f06f-127">Ta wartość powinna być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="9f06f-127">This value should be larger than zero.</span></span> <span data-ttu-id="9f06f-128">Wartość domyślna to 128.</span><span class="sxs-lookup"><span data-stu-id="9f06f-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="9f06f-129">Gdy atrybut powiązania jest ustawiony na `username`, nazwa użytkownika jest mapowana na konta systemu Windows. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="9f06f-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="9f06f-130">Można przesłonić to zachowanie przy użyciu tego atrybutu, który jest ciągiem zawierającym nazwę <xref:System.Web.Security.MembershipProvider> wartości, która zapewnia odpowiedni mechanizm walidacji hasła.</span><span class="sxs-lookup"><span data-stu-id="9f06f-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="9f06f-131">Określa sposób sprawdzania poprawności hasła nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f06f-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="9f06f-132">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9f06f-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="9f06f-133">— System Windows</span><span class="sxs-lookup"><span data-stu-id="9f06f-133">-   Windows</span></span><br /><span data-ttu-id="9f06f-134">- MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="9f06f-134">-   MembershipProvider</span></span><br /><span data-ttu-id="9f06f-135">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9f06f-135">-   Custom</span></span><br /><br /> <span data-ttu-id="9f06f-136">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="9f06f-136">The default is Windows.</span></span> <span data-ttu-id="9f06f-137">Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="9f06f-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f06f-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f06f-138">Child Elements</span></span>  
 <span data-ttu-id="9f06f-139">Brak.</span><span class="sxs-lookup"><span data-stu-id="9f06f-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f06f-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9f06f-140">Parent Elements</span></span>  
  
|<span data-ttu-id="9f06f-141">Element</span><span class="sxs-lookup"><span data-stu-id="9f06f-141">Element</span></span>|<span data-ttu-id="9f06f-142">Opis</span><span class="sxs-lookup"><span data-stu-id="9f06f-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f06f-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9f06f-143">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="9f06f-144">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi oraz ustawienia powiązane z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="9f06f-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f06f-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f06f-145">Remarks</span></span>  
 <span data-ttu-id="9f06f-146">Jeśli żaden z powiązań używanych przez usługę nie jest skonfigurowany do uwierzytelniania opartego na nazwie użytkownika/hasła, atrybuty tego elementu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9f06f-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="9f06f-147">Należą `customUserNamePasswordValidatorType`do nich `includeWindowsGroups`, `membershipProviderName`,, `userNamePasswordValidationMode`i.</span><span class="sxs-lookup"><span data-stu-id="9f06f-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="9f06f-148">Jeśli żaden z powiązań używanych przez usługę nie jest skonfigurowany do korzystania z uwierzytelniania systemu Windows dla nazwy użytkownika/hasła, ustawienia związane z buforowaniem tokenów logowania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9f06f-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="9f06f-149">Należą do `cacheLogonTokenLifetime`nich, `cacheLogonTokens`i. `maxCacheLogonTokens`</span><span class="sxs-lookup"><span data-stu-id="9f06f-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f06f-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f06f-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
