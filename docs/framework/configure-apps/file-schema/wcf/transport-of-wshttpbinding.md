---
title: <transport> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732737"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="bd5e8-102">\<transport> dla \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bd5e8-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="bd5e8-103">Definiuje ustawienia uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="bd5e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd5e8-104">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="bd5e8-105">Typ</span><span class="sxs-lookup"><span data-stu-id="bd5e8-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="bd5e8-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bd5e8-106">Attributes and Elements</span></span>

<span data-ttu-id="bd5e8-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd5e8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd5e8-108">Attributes</span></span>

|<span data-ttu-id="bd5e8-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bd5e8-109">Attribute</span></span>|<span data-ttu-id="bd5e8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bd5e8-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="bd5e8-111">Określa poświadczenie używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="bd5e8-112">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="bd5e8-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="bd5e8-113">Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="bd5e8-114">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="bd5e8-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="bd5e8-115">Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="bd5e8-116">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="bd5e8-117">Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="bd5e8-118">Można również określić kolekcję użytkowników, którzy mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="bd5e8-119">Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="bd5e8-120">To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="bd5e8-121">1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="bd5e8-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="bd5e8-122">2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="bd5e8-123">3. zawsze — zasady są zawsze wymuszane.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="bd5e8-124">Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="bd5e8-125">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="bd5e8-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="bd5e8-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="bd5e8-126">Value</span></span>|<span data-ttu-id="bd5e8-127">Opis</span><span class="sxs-lookup"><span data-stu-id="bd5e8-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="bd5e8-128">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="bd5e8-129">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="bd5e8-130">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="bd5e8-131">Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="bd5e8-132">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="bd5e8-133">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="bd5e8-134">proxyCredentialType — atrybut</span><span class="sxs-lookup"><span data-stu-id="bd5e8-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="bd5e8-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="bd5e8-135">Value</span></span>|<span data-ttu-id="bd5e8-136">Opis</span><span class="sxs-lookup"><span data-stu-id="bd5e8-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="bd5e8-137">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="bd5e8-138">Używa uwierzytelniania podstawowego.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="bd5e8-139">Używa uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="bd5e8-140">Używa protokołu NTLM jako rezerwy z domeną systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="bd5e8-141">Używa zintegrowanego uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="bd5e8-142">Uwierzytelnia klienta za pomocą certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bd5e8-143">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bd5e8-143">Child Elements</span></span>

<span data-ttu-id="bd5e8-144">Brak.</span><span class="sxs-lookup"><span data-stu-id="bd5e8-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd5e8-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bd5e8-145">Parent Elements</span></span>

|<span data-ttu-id="bd5e8-146">Element</span><span class="sxs-lookup"><span data-stu-id="bd5e8-146">Element</span></span>|<span data-ttu-id="bd5e8-147">Opis</span><span class="sxs-lookup"><span data-stu-id="bd5e8-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="bd5e8-148">Reprezentuje możliwości zabezpieczeń [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="bd5e8-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="bd5e8-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd5e8-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="bd5e8-150">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bd5e8-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bd5e8-151">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bd5e8-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bd5e8-152">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="bd5e8-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bd5e8-153">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="bd5e8-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
