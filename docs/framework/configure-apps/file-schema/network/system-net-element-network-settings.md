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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154559"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="052dd-102">\<system.Net>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="052dd-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="052dd-103">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="052dd-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="052dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="052dd-104">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="052dd-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="052dd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="052dd-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="052dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="052dd-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="052dd-107">Attributes</span></span>  
 <span data-ttu-id="052dd-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="052dd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="052dd-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="052dd-109">Child Elements</span></span>  
  
|<span data-ttu-id="052dd-110">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="052dd-110">**Element**</span></span>|<span data-ttu-id="052dd-111">**Opis**</span><span class="sxs-lookup"><span data-stu-id="052dd-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="052dd-112">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="052dd-112">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="052dd-113">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="052dd-113">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="052dd-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="052dd-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="052dd-115">Określa maksymalną liczbę połączeń z hostem internetowym.</span><span class="sxs-lookup"><span data-stu-id="052dd-115">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="052dd-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="052dd-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="052dd-117">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="052dd-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="052dd-118">mailSettings</span><span class="sxs-lookup"><span data-stu-id="052dd-118">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="052dd-119">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="052dd-119">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="052dd-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="052dd-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="052dd-121">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="052dd-121">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="052dd-122">ustawienia</span><span class="sxs-lookup"><span data-stu-id="052dd-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="052dd-123">Konfiguruje podstawowe opcje sieci dla klas w <xref:System.Net> i powiązanych podrzędnych obszarach nazw.</span><span class="sxs-lookup"><span data-stu-id="052dd-123">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="052dd-124">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="052dd-124">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="052dd-125">Określa moduły, które mają być używane do żądania informacji z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="052dd-125">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="052dd-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="052dd-126">Parent Elements</span></span>  
  
|<span data-ttu-id="052dd-127">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="052dd-127">**Element**</span></span>|<span data-ttu-id="052dd-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="052dd-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="052dd-129">skonfigurować</span><span class="sxs-lookup"><span data-stu-id="052dd-129">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="052dd-130">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="052dd-130">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="052dd-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="052dd-131">Remarks</span></span>  
 <span data-ttu-id="052dd-132">[\<system.net>](system-net-element-network-settings.md)Element zawiera ustawienia dla klas z <xref:System.Net> i powiązane podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="052dd-132">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="052dd-133">Ustawienia Konfiguruj moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądania internetowe, aby otrzymywać informacje z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="052dd-133">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="052dd-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="052dd-134">Example</span></span>  
 <span data-ttu-id="052dd-135">Poniższy przykład przedstawia typową konfigurację używaną przez <xref:System.Net> klasy.</span><span class="sxs-lookup"><span data-stu-id="052dd-135">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="052dd-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="052dd-136">See also</span></span>

- [<span data-ttu-id="052dd-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="052dd-137">Network Settings Schema</span></span>](index.md)
