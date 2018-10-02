---
title: '&lt;ServicePointManager —&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2aaf590975d9fd3f5d78cb64d8d2b1c38c0e8dc7
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033509"
---
# <a name="ltservicepointmanagergt-element-network-settings"></a><span data-ttu-id="5658a-102">&lt;ServicePointManager —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="5658a-102">&lt;servicePointManager&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5658a-103">Służy do konfigurowania połączeń z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="5658a-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="5658a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5658a-104">\<configuration></span></span>  
<span data-ttu-id="5658a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5658a-105">\<system.net></span></span>  
<span data-ttu-id="5658a-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="5658a-106">\<settings></span></span>  
<span data-ttu-id="5658a-107">\<ServicePointManager — ></span><span class="sxs-lookup"><span data-stu-id="5658a-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5658a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5658a-108">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5658a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5658a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5658a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5658a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5658a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5658a-111">Attributes</span></span>  
  
|<span data-ttu-id="5658a-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="5658a-112">**Attribute**</span></span>|<span data-ttu-id="5658a-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5658a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="5658a-114">Określa, czy system należy sprawdzić, czy nazwa w certyfikacie jest zgodna nazwa hosta serwera przed rozpoczęciem korzystania z certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5658a-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="5658a-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="5658a-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="5658a-116">Określa, czy system należy sprawdzić, czy certyfikat został odwołany przed rozpoczęciem korzystania z certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5658a-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="5658a-117">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5658a-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="5658a-118">Określa, ile domeny nazwa usługi (DNS) rozwiązania są buforowane w połączeniu z opcją DNS okrężnego w milisekundach.</span><span class="sxs-lookup"><span data-stu-id="5658a-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="5658a-119">Wartość domyślna to 120 000 milisekund (dwie minuty).</span><span class="sxs-lookup"><span data-stu-id="5658a-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="5658a-120">Określa, czy nazwy rozwiązania DNS hosta z wieloma adresami Internet Protocol (IP), zwracany, wszystkie adresy lub tylko pierwszy z nich.</span><span class="sxs-lookup"><span data-stu-id="5658a-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="5658a-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5658a-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="5658a-122">Określa zasady szyfrowania, zastosowane do sesji SSL/TLS w <xref:System.Net.ServicePointManager> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5658a-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="5658a-123">Możliwe wartości to odpowiednikiem wartości <xref:System.Net.Security.EncryptionPolicy> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5658a-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="5658a-124">Korzystanie z <xref:System.Security.Authentication.CipherAlgorithmType.Null> jest wymagany, jeśli ustawiono zasady szyfrowania `NoEncryption`.</span><span class="sxs-lookup"><span data-stu-id="5658a-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="5658a-125">Wartość domyślna to `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="5658a-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="5658a-126">Określa, czy metody POST należy się spodziewać otrzymać `100-continue` odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="5658a-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="5658a-127">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="5658a-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="5658a-128">Określa, czy kontrolowane przez usługę Menedżer punktu połączenia używają algorytmu Nagle'a.</span><span class="sxs-lookup"><span data-stu-id="5658a-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="5658a-129">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="5658a-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5658a-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5658a-130">Child Elements</span></span>  
 <span data-ttu-id="5658a-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="5658a-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5658a-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5658a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5658a-133">**Element**</span><span class="sxs-lookup"><span data-stu-id="5658a-133">**Element**</span></span>|<span data-ttu-id="5658a-134">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5658a-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5658a-135">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="5658a-135">Settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="5658a-136">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5658a-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5658a-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5658a-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5658a-138">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5658a-138">Configuration Files</span></span>  
 <span data-ttu-id="5658a-139">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5658a-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5658a-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5658a-140">See Also</span></span>  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [<span data-ttu-id="5658a-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="5658a-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
