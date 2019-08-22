---
title: <system.Net>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 449146612938700f59f5e2ec761526d1dc66a3fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663957"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="70c63-102">\<System .net >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="70c63-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="70c63-103">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="70c63-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="70c63-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="70c63-104">\<configuration></span></span>  
<span data-ttu-id="70c63-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="70c63-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c63-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="70c63-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70c63-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70c63-107">Attributes and Elements</span></span>  
 <span data-ttu-id="70c63-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70c63-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70c63-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70c63-109">Attributes</span></span>  
 <span data-ttu-id="70c63-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="70c63-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70c63-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70c63-111">Child Elements</span></span>  
  
|<span data-ttu-id="70c63-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="70c63-112">**Element**</span></span>|<span data-ttu-id="70c63-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="70c63-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70c63-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="70c63-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="70c63-115">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="70c63-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="70c63-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="70c63-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="70c63-117">Określa maksymalną liczbę połączeń z hostem internetowym.</span><span class="sxs-lookup"><span data-stu-id="70c63-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="70c63-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="70c63-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="70c63-119">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="70c63-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="70c63-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="70c63-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="70c63-121">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="70c63-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="70c63-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="70c63-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="70c63-123">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="70c63-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="70c63-124">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="70c63-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="70c63-125">Konfiguruje podstawowe opcje sieci dla klas w <xref:System.Net> i powiązanych podrzędnych obszarach nazw.</span><span class="sxs-lookup"><span data-stu-id="70c63-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="70c63-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="70c63-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="70c63-127">Określa moduły, które mają być używane do żądania informacji z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="70c63-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70c63-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70c63-128">Parent Elements</span></span>  
  
|<span data-ttu-id="70c63-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="70c63-129">**Element**</span></span>|<span data-ttu-id="70c63-130">**Opis**</span><span class="sxs-lookup"><span data-stu-id="70c63-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70c63-131">skonfigurować</span><span class="sxs-lookup"><span data-stu-id="70c63-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="70c63-132">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="70c63-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c63-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70c63-133">Remarks</span></span>  
 <span data-ttu-id="70c63-134"><xref:System.Net> [ ElementSystem.net>zawieraustawieniadlaklaswi\<](system-net-element-network-settings.md) powiązanych podrzędnych obszarach nazw.</span><span class="sxs-lookup"><span data-stu-id="70c63-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="70c63-135">Ustawienia Konfiguruj moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądania internetowe, aby otrzymywać informacje z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="70c63-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c63-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="70c63-136">Example</span></span>  
 <span data-ttu-id="70c63-137">Poniższy przykład przedstawia typową konfigurację używaną przez <xref:System.Net> klasy.</span><span class="sxs-lookup"><span data-stu-id="70c63-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="70c63-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70c63-138">See also</span></span>

- [<span data-ttu-id="70c63-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="70c63-139">Network Settings Schema</span></span>](index.md)
