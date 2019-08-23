---
title: <transport> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 384267e3d018d714f95356461eb303bc9ec0cb3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934636"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="9e200-102">\<Transport > \<WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9e200-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="9e200-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9e200-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="9e200-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9e200-104">\<system.serviceModel></span></span>\
<span data-ttu-id="9e200-105">\<powiązania > </span><span class="sxs-lookup"><span data-stu-id="9e200-105">\<bindings></span></span>\
<span data-ttu-id="9e200-106">\<wsHttpBinding > </span><span class="sxs-lookup"><span data-stu-id="9e200-106">\<wsHttpBinding></span></span>\
<span data-ttu-id="9e200-107">\<> powiązania </span><span class="sxs-lookup"><span data-stu-id="9e200-107">\<binding></span></span>\
<span data-ttu-id="9e200-108">\<> zabezpieczeń </span><span class="sxs-lookup"><span data-stu-id="9e200-108">\<security></span></span>\
<span data-ttu-id="9e200-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="9e200-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="9e200-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e200-110">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="9e200-111">Typ</span><span class="sxs-lookup"><span data-stu-id="9e200-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="9e200-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e200-112">Attributes and Elements</span></span>

<span data-ttu-id="9e200-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9e200-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e200-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e200-114">Attributes</span></span>

|<span data-ttu-id="9e200-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9e200-115">Attribute</span></span>|<span data-ttu-id="9e200-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9e200-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="9e200-117">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="9e200-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="9e200-118">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9e200-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="9e200-119">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="9e200-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="9e200-120">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9e200-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="9e200-121">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9e200-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="9e200-122">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9e200-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9e200-123">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="9e200-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="9e200-124">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="9e200-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="9e200-125">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="9e200-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="9e200-126">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="9e200-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="9e200-127">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="9e200-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="9e200-128">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="9e200-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="9e200-129">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="9e200-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="9e200-130">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="9e200-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9e200-131">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="9e200-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="9e200-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="9e200-132">Value</span></span>|<span data-ttu-id="9e200-133">Opis</span><span class="sxs-lookup"><span data-stu-id="9e200-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="9e200-134">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="9e200-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="9e200-135">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9e200-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="9e200-136">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="9e200-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="9e200-137">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e200-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="9e200-138">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e200-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="9e200-139">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="9e200-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="9e200-140">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="9e200-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="9e200-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="9e200-141">Value</span></span>|<span data-ttu-id="9e200-142">Opis</span><span class="sxs-lookup"><span data-stu-id="9e200-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="9e200-143">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="9e200-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="9e200-144">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9e200-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="9e200-145">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="9e200-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="9e200-146">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e200-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="9e200-147">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e200-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="9e200-148">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="9e200-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9e200-149">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e200-149">Child Elements</span></span>

<span data-ttu-id="9e200-150">Brak.</span><span class="sxs-lookup"><span data-stu-id="9e200-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9e200-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e200-151">Parent Elements</span></span>

|<span data-ttu-id="9e200-152">Element</span><span class="sxs-lookup"><span data-stu-id="9e200-152">Element</span></span>|<span data-ttu-id="9e200-153">Opis</span><span class="sxs-lookup"><span data-stu-id="9e200-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e200-154">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9e200-154">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="9e200-155">Reprezentuje możliwości [ \<zabezpieczeń > WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9e200-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="9e200-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e200-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="9e200-157">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9e200-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9e200-158">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9e200-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9e200-159">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="9e200-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9e200-160">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="9e200-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9e200-161">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9e200-161">\<binding></span></span>](../../../misc/binding.md)
