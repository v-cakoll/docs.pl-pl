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
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697507"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="d214b-102">\<system .net >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="d214b-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="d214b-103">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="d214b-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="d214b-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="d214b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d214b-105">&nbsp; @ no__t-1 **@no__t -3system. net >**</span><span class="sxs-lookup"><span data-stu-id="d214b-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d214b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d214b-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d214b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d214b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d214b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d214b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d214b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d214b-109">Attributes</span></span>  
 <span data-ttu-id="d214b-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d214b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d214b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d214b-111">Child Elements</span></span>  
  
|<span data-ttu-id="d214b-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="d214b-112">**Element**</span></span>|<span data-ttu-id="d214b-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d214b-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d214b-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d214b-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d214b-115">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="d214b-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="d214b-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d214b-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="d214b-117">Określa maksymalną liczbę połączeń z hostem internetowym.</span><span class="sxs-lookup"><span data-stu-id="d214b-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="d214b-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d214b-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="d214b-119">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="d214b-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="d214b-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="d214b-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="d214b-121">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="d214b-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="d214b-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="d214b-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="d214b-123">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="d214b-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="d214b-124">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="d214b-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="d214b-125">Konfiguruje podstawowe opcje sieci dla klas w <xref:System.Net> i pokrewnych podrzędnych obszarach nazw.</span><span class="sxs-lookup"><span data-stu-id="d214b-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="d214b-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d214b-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="d214b-127">Określa moduły, które mają być używane do żądania informacji z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="d214b-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d214b-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d214b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d214b-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="d214b-129">**Element**</span></span>|<span data-ttu-id="d214b-130">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d214b-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d214b-131">skonfigurować</span><span class="sxs-lookup"><span data-stu-id="d214b-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="d214b-132">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d214b-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d214b-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d214b-133">Remarks</span></span>  
 <span data-ttu-id="d214b-134">Element [@no__t -1System. net >](system-net-element-network-settings.md) zawiera ustawienia dla klas w <xref:System.Net> i powiązanych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="d214b-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="d214b-135">Ustawienia Konfiguruj moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądania internetowe, aby otrzymywać informacje z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="d214b-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d214b-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="d214b-136">Example</span></span>  
 <span data-ttu-id="d214b-137">W poniższym przykładzie przedstawiono typową konfigurację używaną przez klasy <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="d214b-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d214b-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d214b-138">See also</span></span>

- [<span data-ttu-id="d214b-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d214b-139">Network Settings Schema</span></span>](index.md)
