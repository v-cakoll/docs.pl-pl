---
title: <transport> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 95cfa076f62f767af431ff5a0bcc2ca31b824e30
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399244"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="94606-102">\<Transport > \<WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="94606-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="94606-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="94606-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="94606-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94606-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94606-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="94606-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="94606-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="94606-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="94606-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="94606-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="94606-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="94606-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="94606-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="94606-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="94606-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transportu**</span><span class="sxs-lookup"><span data-stu-id="94606-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="94606-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="94606-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="94606-112">Typ</span><span class="sxs-lookup"><span data-stu-id="94606-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="94606-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="94606-113">Attributes and Elements</span></span>

<span data-ttu-id="94606-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="94606-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="94606-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94606-115">Attributes</span></span>

|<span data-ttu-id="94606-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="94606-116">Attribute</span></span>|<span data-ttu-id="94606-117">Opis</span><span class="sxs-lookup"><span data-stu-id="94606-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="94606-118">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="94606-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="94606-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="94606-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="94606-120">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="94606-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="94606-121">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="94606-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="94606-122">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="94606-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="94606-123">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="94606-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="94606-124">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="94606-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="94606-125">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="94606-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="94606-126">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="94606-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="94606-127">To Wyliczenie określa, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Kiedy należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="94606-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="94606-128">1.  Nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="94606-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="94606-129">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="94606-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="94606-130">3.  Zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="94606-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="94606-131">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="94606-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="94606-132">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="94606-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="94606-133">Wartość</span><span class="sxs-lookup"><span data-stu-id="94606-133">Value</span></span>|<span data-ttu-id="94606-134">Opis</span><span class="sxs-lookup"><span data-stu-id="94606-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="94606-135">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="94606-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="94606-136">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="94606-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="94606-137">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="94606-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="94606-138">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94606-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="94606-139">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94606-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="94606-140">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="94606-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="94606-141">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="94606-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="94606-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="94606-142">Value</span></span>|<span data-ttu-id="94606-143">Opis</span><span class="sxs-lookup"><span data-stu-id="94606-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="94606-144">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="94606-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="94606-145">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="94606-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="94606-146">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="94606-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="94606-147">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94606-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="94606-148">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94606-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="94606-149">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="94606-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="94606-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94606-150">Child Elements</span></span>

<span data-ttu-id="94606-151">Brak.</span><span class="sxs-lookup"><span data-stu-id="94606-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94606-152">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="94606-152">Parent Elements</span></span>

|<span data-ttu-id="94606-153">Element</span><span class="sxs-lookup"><span data-stu-id="94606-153">Element</span></span>|<span data-ttu-id="94606-154">Opis</span><span class="sxs-lookup"><span data-stu-id="94606-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94606-155">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="94606-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="94606-156">Reprezentuje możliwości [ \<zabezpieczeń > WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94606-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="94606-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94606-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="94606-158">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="94606-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="94606-159">Powiązania</span><span class="sxs-lookup"><span data-stu-id="94606-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="94606-160">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="94606-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="94606-161">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="94606-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="94606-162">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="94606-162">\<binding></span></span>](../../../misc/binding.md)
