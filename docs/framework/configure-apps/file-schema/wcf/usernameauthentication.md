---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 5a4cf8d429198b889f2bb362294ba3841c814b26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083148"
---
# <a name="usernameauthentication"></a><span data-ttu-id="890d2-101">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="890d2-101">\<userNameAuthentication></span></span>
<span data-ttu-id="890d2-102">Określa poświadczenia usługi, w oparciu o nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="890d2-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="890d2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="890d2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="890d2-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="890d2-104">\<behaviors></span></span>  
<span data-ttu-id="890d2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="890d2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="890d2-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="890d2-106">\<behavior></span></span>  
<span data-ttu-id="890d2-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="890d2-107">\<serviceCredentials></span></span>  
<span data-ttu-id="890d2-108">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="890d2-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="890d2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="890d2-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="890d2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="890d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="890d2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="890d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="890d2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="890d2-112">Attributes</span></span>  
  
|<span data-ttu-id="890d2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="890d2-113">Attribute</span></span>|<span data-ttu-id="890d2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="890d2-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="890d2-115">Element <xref:System.TimeSpan> , który określa maksymalną długość czasu, jest buforowany token.</span><span class="sxs-lookup"><span data-stu-id="890d2-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="890d2-116">Wartość domyślna to 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="890d2-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="890d2-117">Wartość logiczna określająca, czy tokeny logowania są buforowane.</span><span class="sxs-lookup"><span data-stu-id="890d2-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="890d2-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="890d2-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="890d2-119">Ciąg, który określa typ modułu weryfikacji hasła niestandardowej nazwy użytkownika do użycia.</span><span class="sxs-lookup"><span data-stu-id="890d2-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="890d2-120">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="890d2-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="890d2-121">Wartość logiczna określająca, czy grupy Windows znajdują się w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="890d2-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="890d2-122">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="890d2-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="890d2-123">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona wystąpił błąd rozszerzania grupy pełnej.</span><span class="sxs-lookup"><span data-stu-id="890d2-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="890d2-124">Ustaw tę właściwość na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="890d2-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="890d2-125">Liczba całkowita określająca maksymalną liczbę tokenów logowania do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="890d2-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="890d2-126">Ta wartość powinna być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="890d2-126">This value should be larger than zero.</span></span> <span data-ttu-id="890d2-127">Wartość domyślna to 128.</span><span class="sxs-lookup"><span data-stu-id="890d2-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="890d2-128">Gdy `clientCredentialType` ma ustawioną wartość atrybutu powiązania `username`, nazwa użytkownika jest mapowany do konta Windows.</span><span class="sxs-lookup"><span data-stu-id="890d2-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="890d2-129">Można zastąpić to zachowanie za pomocą tego atrybutu jest ciąg zawierający nazwę <xref:System.Web.Security.MembershipProvider> wartość, która zawiera odpowiednie hasło mechanizmu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="890d2-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="890d2-130">Określa sposób, w których nazwy użytkownika hasło jest weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="890d2-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="890d2-131">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="890d2-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="890d2-132">— Windows</span><span class="sxs-lookup"><span data-stu-id="890d2-132">-   Windows</span></span><br /><span data-ttu-id="890d2-133">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="890d2-133">-   MembershipProvider</span></span><br /><span data-ttu-id="890d2-134">— Niestandardowa</span><span class="sxs-lookup"><span data-stu-id="890d2-134">-   Custom</span></span><br /><br /> <span data-ttu-id="890d2-135">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="890d2-135">The default is Windows.</span></span> <span data-ttu-id="890d2-136">Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="890d2-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="890d2-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="890d2-137">Child Elements</span></span>  
 <span data-ttu-id="890d2-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="890d2-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="890d2-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="890d2-139">Parent Elements</span></span>  
  
|<span data-ttu-id="890d2-140">Element</span><span class="sxs-lookup"><span data-stu-id="890d2-140">Element</span></span>|<span data-ttu-id="890d2-141">Opis</span><span class="sxs-lookup"><span data-stu-id="890d2-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="890d2-142">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="890d2-142">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="890d2-143">Określa poświadczenie do użycia w uwierzytelnianiu usługi i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="890d2-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="890d2-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="890d2-144">Remarks</span></span>  
 <span data-ttu-id="890d2-145">Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania opartego na nazwie/hasło użytkownika, atrybuty dla tego elementu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="890d2-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="890d2-146">Obejmują one `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, i `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="890d2-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="890d2-147">Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do używania uwierzytelniania Windows dla nazwy użytkownika i hasła, ustawienia związane z buforowaniem tokeny logowania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="890d2-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="890d2-148">Obejmują one `cacheLogonTokenLifetime`, `cacheLogonTokens`, i `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="890d2-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890d2-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="890d2-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
