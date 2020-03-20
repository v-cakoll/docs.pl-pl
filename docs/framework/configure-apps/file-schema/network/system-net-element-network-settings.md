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
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154559"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="a4974-102">\<system.Net element> (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="a4974-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="a4974-103">Zawiera ustawienia określające sposób łączenia się programu .NET Framework z siecią.</span><span class="sxs-lookup"><span data-stu-id="a4974-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="a4974-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="a4974-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a4974-105">&nbsp;&nbsp;**\<system.net>**</span><span class="sxs-lookup"><span data-stu-id="a4974-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4974-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4974-106">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4974-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a4974-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a4974-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a4974-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4974-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a4974-109">Attributes</span></span>  
 <span data-ttu-id="a4974-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="a4974-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4974-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a4974-111">Child Elements</span></span>  
  
|<span data-ttu-id="a4974-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="a4974-112">**Element**</span></span>|<span data-ttu-id="a4974-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a4974-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a4974-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a4974-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="a4974-115">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="a4974-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="a4974-116">connectionManagement (PołączenieManagement)</span><span class="sxs-lookup"><span data-stu-id="a4974-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a4974-117">Określa maksymalną liczbę połączeń z hostem internetowym.</span><span class="sxs-lookup"><span data-stu-id="a4974-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="a4974-118">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="a4974-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a4974-119">Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).</span><span class="sxs-lookup"><span data-stu-id="a4974-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="a4974-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="a4974-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="a4974-121">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="a4974-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="a4974-122">requestCaching (Buforowanie)</span><span class="sxs-lookup"><span data-stu-id="a4974-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="a4974-123">Steruje mechanizmem buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="a4974-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="a4974-124">ustawienia</span><span class="sxs-lookup"><span data-stu-id="a4974-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a4974-125">Konfiguruje podstawowe opcje sieciowe dla klas w <xref:System.Net> powiązanych podrzędnych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="a4974-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="a4974-126">webRequestModules (WebRequestModules)</span><span class="sxs-lookup"><span data-stu-id="a4974-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="a4974-127">Określa moduły, za pomocą których mają być wymagane informacje od hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="a4974-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4974-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a4974-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a4974-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="a4974-129">**Element**</span></span>|<span data-ttu-id="a4974-130">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a4974-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a4974-131">Konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a4974-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="a4974-132">Zawiera ustawienia dla wszystkich obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="a4974-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4974-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4974-133">Remarks</span></span>  
 <span data-ttu-id="a4974-134">[ \<System.net>](system-net-element-network-settings.md) element zawiera ustawienia dla klas w <xref:System.Net> i powiązanych przestrzeni nazw podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a4974-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="a4974-135">Ustawienia konfigurują moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądań internetowych do odbierania informacji z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="a4974-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4974-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4974-136">Example</span></span>  
 <span data-ttu-id="a4974-137">Poniższy przykład przedstawia typową <xref:System.Net> konfigurację używaną przez klasy.</span><span class="sxs-lookup"><span data-stu-id="a4974-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4974-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4974-138">See also</span></span>

- [<span data-ttu-id="a4974-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a4974-139">Network Settings Schema</span></span>](index.md)
