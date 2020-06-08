---
title: <servicePointManager>, element (ustawienia sieci)
description: <servicePointManager>Element ustawień sieciowych konfiguruje połączenia z opcjami zasobów sieciowych w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504527"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="2cc1f-103">\<servicePointManager>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="2cc1f-103">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="2cc1f-104">Konfiguruje połączenia z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="2cc1f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cc1f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cc1f-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2cc1f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2cc1f-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cc1f-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2cc1f-108">Attributes</span></span>  
  
|<span data-ttu-id="2cc1f-109">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="2cc1f-109">**Attribute**</span></span>|<span data-ttu-id="2cc1f-110">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2cc1f-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="2cc1f-111">Określa, czy przed użyciem certyfikatu system powinien sprawdzić, czy nazwa certyfikatu jest zgodna z nazwą hosta serwera.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="2cc1f-112">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="2cc1f-113">Określa, czy system powinien sprawdzić, czy certyfikat został odwołany przed użyciem certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="2cc1f-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="2cc1f-115">Określa, jak długo w milisekundach jest buforowanych rozwiązań usługi nazw domen (DNS) w połączeniu z opcją działania okrężnego systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="2cc1f-116">Wartość domyślna to 120 000 milisekund (dwie minuty).</span><span class="sxs-lookup"><span data-stu-id="2cc1f-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="2cc1f-117">Określa, czy rozwiązania DNS nazw hostów z wieloma adresami IP (Internet Protocol) zwracają wszystkie adresy, czy tylko pierwszy.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="2cc1f-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="2cc1f-119">Określa zasady szyfrowania stosowane do sesji SSL/TLS w <xref:System.Net.ServicePointManager> wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="2cc1f-120">Możliwe wartości są równoważne z wartościami <xref:System.Net.Security.EncryptionPolicy> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="2cc1f-121">Użycie <xref:System.Security.Authentication.CipherAlgorithmType.Null> jest wymagane, gdy zasady szyfrowania są ustawione na `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="2cc1f-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="2cc1f-122">Wartość domyślna to `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="2cc1f-123">Określa, czy metody POST powinny oczekiwać `100-continue` odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="2cc1f-124">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="2cc1f-125">Określa, czy połączenia kontrolowane przez Menedżera punktów usług używają algorytmu nagle.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="2cc1f-126">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cc1f-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2cc1f-127">Child Elements</span></span>  
 <span data-ttu-id="2cc1f-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cc1f-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2cc1f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2cc1f-130">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="2cc1f-130">**Element**</span></span>|<span data-ttu-id="2cc1f-131">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2cc1f-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2cc1f-132">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="2cc1f-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="2cc1f-133">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2cc1f-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cc1f-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cc1f-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2cc1f-135">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2cc1f-135">Configuration Files</span></span>  
 <span data-ttu-id="2cc1f-136">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2cc1f-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc1f-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cc1f-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="2cc1f-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2cc1f-138">Network Settings Schema</span></span>](index.md)
