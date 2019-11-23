---
title: <webRequestModules>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697463"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="c80ef-102">\<element > webRequestModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c80ef-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="c80ef-103">Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="c80ef-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="c80ef-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="c80ef-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c80ef-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c80ef-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="c80ef-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="c80ef-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80ef-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c80ef-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c80ef-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c80ef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c80ef-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c80ef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c80ef-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c80ef-110">Attributes</span></span>  
 <span data-ttu-id="c80ef-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="c80ef-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c80ef-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c80ef-112">Child Elements</span></span>  
  
|<span data-ttu-id="c80ef-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="c80ef-113">**Element**</span></span>|<span data-ttu-id="c80ef-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c80ef-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c80ef-115">add</span><span class="sxs-lookup"><span data-stu-id="c80ef-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c80ef-116">Dodaje niestandardowy moduł żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c80ef-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="c80ef-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="c80ef-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c80ef-118">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c80ef-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="c80ef-119">remove</span><span class="sxs-lookup"><span data-stu-id="c80ef-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c80ef-120">Usuwa niestandardowy moduł żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c80ef-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c80ef-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c80ef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c80ef-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="c80ef-122">**Element**</span></span>|<span data-ttu-id="c80ef-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c80ef-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c80ef-124">system.net</span><span class="sxs-lookup"><span data-stu-id="c80ef-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c80ef-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="c80ef-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c80ef-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c80ef-126">Remarks</span></span>  
 <span data-ttu-id="c80ef-127">Element `webRequestModules` rejestruje elementy podrzędne klasy <xref:System.Net.WebRequest> do obsługi żądań informacji do hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="c80ef-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="c80ef-128">Moduły żądania sieci Web muszą implementować interfejs <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="c80ef-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="c80ef-129">.NET Framework obejmuje moduły żądania sieci Web dla identyfikatorów URI zaczynających się od `http://`, `https://`i `file://`.</span><span class="sxs-lookup"><span data-stu-id="c80ef-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="c80ef-130">Moduły domyślne można zastąpić tylko przez zarejestrowanie modułu niestandardowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c80ef-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c80ef-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c80ef-131">Configuration Files</span></span>  
 <span data-ttu-id="c80ef-132">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c80ef-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c80ef-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="c80ef-133">Example</span></span>  
 <span data-ttu-id="c80ef-134">Poniższy przykład rejestruje domyślny moduł HTTP.</span><span class="sxs-lookup"><span data-stu-id="c80ef-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="c80ef-135">Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="c80ef-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c80ef-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c80ef-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="c80ef-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c80ef-137">Network Settings Schema</span></span>](index.md)
