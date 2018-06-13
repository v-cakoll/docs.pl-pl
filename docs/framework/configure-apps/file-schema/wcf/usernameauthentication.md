---
title: '&lt;UserNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: d81bf3441f4999683b9dc9ab956fff517c20e80e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754866"
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="28b91-102">&lt;UserNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="28b91-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="28b91-103">Określa poświadczenia usługi na podstawie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="28b91-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="28b91-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28b91-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28b91-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="28b91-105">\<behaviors></span></span>  
<span data-ttu-id="28b91-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="28b91-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="28b91-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="28b91-107">\<behavior></span></span>  
<span data-ttu-id="28b91-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="28b91-108">\<serviceCredentials></span></span>  
<span data-ttu-id="28b91-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="28b91-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b91-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="28b91-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28b91-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28b91-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28b91-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28b91-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28b91-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28b91-113">Attributes</span></span>  
  
|<span data-ttu-id="28b91-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28b91-114">Attribute</span></span>|<span data-ttu-id="28b91-115">Opis</span><span class="sxs-lookup"><span data-stu-id="28b91-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="28b91-116">A <xref:System.TimeSpan> , który określa maksymalną długość czasu tokenu są buforowane.</span><span class="sxs-lookup"><span data-stu-id="28b91-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="28b91-117">Wartość domyślna to 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="28b91-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="28b91-118">Wartość logiczna określająca, czy tokeny logowania są buforowane.</span><span class="sxs-lookup"><span data-stu-id="28b91-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="28b91-119">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="28b91-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="28b91-120">Ciąg określający typ Walidatora niestandardowej nazwy użytkownika hasło do użycia.</span><span class="sxs-lookup"><span data-stu-id="28b91-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="28b91-121">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="28b91-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="28b91-122">Wartość logiczna określająca, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="28b91-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="28b91-123">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="28b91-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="28b91-124">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ jej wynikiem rozszerzenia grupy pełnej.</span><span class="sxs-lookup"><span data-stu-id="28b91-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="28b91-125">Ta właściwość jest ustawiana `false` Jeśli nie musisz ustanowić listę grup należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="28b91-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="28b91-126">Liczba całkowita określająca maksymalną liczbę tokenów logowania do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="28b91-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="28b91-127">Ta wartość powinna być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="28b91-127">This value should be larger than zero.</span></span> <span data-ttu-id="28b91-128">Wartość domyślna to 128.</span><span class="sxs-lookup"><span data-stu-id="28b91-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="28b91-129">Gdy `clientCredentialType` ustawiono atrybut powiązania `username`, nazwa użytkownika jest mapowana na konta systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="28b91-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="28b91-130">Użytkownik może zmienić to zachowanie przy użyciu tego atrybutu, który jest ciąg znaków zawierający nazwę <xref:System.Web.Security.MembershipProvider> wartość, która zapewnia mechanizm weryfikacji odpowiednie hasło.</span><span class="sxs-lookup"><span data-stu-id="28b91-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="28b91-131">Określa sposób, w których nazwy użytkownika hasło jest weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="28b91-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="28b91-132">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="28b91-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="28b91-133">— Windows</span><span class="sxs-lookup"><span data-stu-id="28b91-133">-   Windows</span></span><br /><span data-ttu-id="28b91-134">-MembershipProvider.</span><span class="sxs-lookup"><span data-stu-id="28b91-134">-   MembershipProvider</span></span><br /><span data-ttu-id="28b91-135">-Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="28b91-135">-   Custom</span></span><br /><br /> <span data-ttu-id="28b91-136">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="28b91-136">The default is Windows.</span></span> <span data-ttu-id="28b91-137">Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="28b91-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28b91-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28b91-138">Child Elements</span></span>  
 <span data-ttu-id="28b91-139">Brak.</span><span class="sxs-lookup"><span data-stu-id="28b91-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28b91-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28b91-140">Parent Elements</span></span>  
  
|<span data-ttu-id="28b91-141">Element</span><span class="sxs-lookup"><span data-stu-id="28b91-141">Element</span></span>|<span data-ttu-id="28b91-142">Opis</span><span class="sxs-lookup"><span data-stu-id="28b91-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b91-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="28b91-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="28b91-144">Określa poświadczenia, które ma być używany podczas uwierzytelniania usługi, i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="28b91-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28b91-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28b91-145">Remarks</span></span>  
 <span data-ttu-id="28b91-146">Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania opartego na nazwie/hasło użytkownika, są ignorowane atrybutów dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="28b91-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="28b91-147">Obejmują one `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, i `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="28b91-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="28b91-148">Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania systemu Windows dla nazwy użytkownika i hasła, ustawienia związane z buforowaniem tokenów logowania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="28b91-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="28b91-149">Obejmują one `cacheLogonTokenLifetime`, `cacheLogonTokens`, i `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="28b91-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b91-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28b91-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
