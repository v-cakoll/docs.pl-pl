---
title: '&lt;userNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 1b8a85a3b2699aa88db24d1f7afee3de67dbf39b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656651"
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="abaaa-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="abaaa-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="abaaa-103">Określa poświadczenia usługi, w oparciu o nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="abaaa-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="abaaa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="abaaa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="abaaa-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="abaaa-105">\<behaviors></span></span>  
<span data-ttu-id="abaaa-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="abaaa-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="abaaa-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="abaaa-107">\<behavior></span></span>  
<span data-ttu-id="abaaa-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="abaaa-108">\<serviceCredentials></span></span>  
<span data-ttu-id="abaaa-109">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="abaaa-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abaaa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="abaaa-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abaaa-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="abaaa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="abaaa-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="abaaa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abaaa-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="abaaa-113">Attributes</span></span>  
  
|<span data-ttu-id="abaaa-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="abaaa-114">Attribute</span></span>|<span data-ttu-id="abaaa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="abaaa-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="abaaa-116">Element <xref:System.TimeSpan> , który określa maksymalną długość czasu, jest buforowany token.</span><span class="sxs-lookup"><span data-stu-id="abaaa-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="abaaa-117">Wartość domyślna to 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="abaaa-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="abaaa-118">Wartość logiczna określająca, czy tokeny logowania są buforowane.</span><span class="sxs-lookup"><span data-stu-id="abaaa-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="abaaa-119">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="abaaa-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="abaaa-120">Ciąg, który określa typ modułu weryfikacji hasła niestandardowej nazwy użytkownika do użycia.</span><span class="sxs-lookup"><span data-stu-id="abaaa-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="abaaa-121">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abaaa-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="abaaa-122">Wartość logiczna określająca, czy grupy Windows znajdują się w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="abaaa-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="abaaa-123">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="abaaa-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="abaaa-124">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona wystąpił błąd rozszerzania grupy pełnej.</span><span class="sxs-lookup"><span data-stu-id="abaaa-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="abaaa-125">Ustaw tę właściwość na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="abaaa-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="abaaa-126">Liczba całkowita określająca maksymalną liczbę tokenów logowania do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="abaaa-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="abaaa-127">Ta wartość powinna być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="abaaa-127">This value should be larger than zero.</span></span> <span data-ttu-id="abaaa-128">Wartość domyślna to 128.</span><span class="sxs-lookup"><span data-stu-id="abaaa-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="abaaa-129">Gdy `clientCredentialType` ma ustawioną wartość atrybutu powiązania `username`, nazwa użytkownika jest mapowany do konta Windows.</span><span class="sxs-lookup"><span data-stu-id="abaaa-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="abaaa-130">Można zastąpić to zachowanie za pomocą tego atrybutu jest ciąg zawierający nazwę <xref:System.Web.Security.MembershipProvider> wartość, która zawiera odpowiednie hasło mechanizmu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="abaaa-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="abaaa-131">Określa sposób, w których nazwy użytkownika hasło jest weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="abaaa-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="abaaa-132">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="abaaa-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="abaaa-133">— Windows</span><span class="sxs-lookup"><span data-stu-id="abaaa-133">-   Windows</span></span><br /><span data-ttu-id="abaaa-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="abaaa-134">-   MembershipProvider</span></span><br /><span data-ttu-id="abaaa-135">— Niestandardowa</span><span class="sxs-lookup"><span data-stu-id="abaaa-135">-   Custom</span></span><br /><br /> <span data-ttu-id="abaaa-136">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="abaaa-136">The default is Windows.</span></span> <span data-ttu-id="abaaa-137">Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="abaaa-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abaaa-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="abaaa-138">Child Elements</span></span>  
 <span data-ttu-id="abaaa-139">Brak.</span><span class="sxs-lookup"><span data-stu-id="abaaa-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abaaa-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="abaaa-140">Parent Elements</span></span>  
  
|<span data-ttu-id="abaaa-141">Element</span><span class="sxs-lookup"><span data-stu-id="abaaa-141">Element</span></span>|<span data-ttu-id="abaaa-142">Opis</span><span class="sxs-lookup"><span data-stu-id="abaaa-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abaaa-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="abaaa-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="abaaa-144">Określa poświadczenie do użycia w uwierzytelnianiu usługi i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="abaaa-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abaaa-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abaaa-145">Remarks</span></span>  
 <span data-ttu-id="abaaa-146">Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania opartego na nazwie/hasło użytkownika, atrybuty dla tego elementu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="abaaa-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="abaaa-147">Obejmują one `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, i `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="abaaa-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="abaaa-148">Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do używania uwierzytelniania Windows dla nazwy użytkownika i hasła, ustawienia związane z buforowaniem tokeny logowania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="abaaa-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="abaaa-149">Obejmują one `cacheLogonTokenLifetime`, `cacheLogonTokens`, i `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="abaaa-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abaaa-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abaaa-150">See also</span></span>
- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
