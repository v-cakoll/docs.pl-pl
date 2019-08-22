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
ms.openlocfilehash: c30a7a0bcce62c99d7c1ec0ff17389b8c2cd2f17
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663943"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="f5dd6-102">\<webRequestModules >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f5dd6-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="f5dd6-103">Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="f5dd6-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f5dd6-104">\<configuration></span></span>  
<span data-ttu-id="f5dd6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f5dd6-105">\<system.net></span></span>  
<span data-ttu-id="f5dd6-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="f5dd6-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5dd6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5dd6-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5dd6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f5dd6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f5dd6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5dd6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f5dd6-110">Attributes</span></span>  
 <span data-ttu-id="f5dd6-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5dd6-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f5dd6-112">Child Elements</span></span>  
  
|<span data-ttu-id="f5dd6-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="f5dd6-113">**Element**</span></span>|<span data-ttu-id="f5dd6-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f5dd6-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f5dd6-115">add</span><span class="sxs-lookup"><span data-stu-id="f5dd6-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="f5dd6-116">Dodaje niestandardowy moduł żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="f5dd6-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="f5dd6-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="f5dd6-118">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="f5dd6-119">remove</span><span class="sxs-lookup"><span data-stu-id="f5dd6-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="f5dd6-120">Usuwa niestandardowy moduł żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5dd6-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f5dd6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f5dd6-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="f5dd6-122">**Element**</span></span>|<span data-ttu-id="f5dd6-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f5dd6-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f5dd6-124">system.net</span><span class="sxs-lookup"><span data-stu-id="f5dd6-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="f5dd6-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5dd6-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5dd6-126">Remarks</span></span>  
 <span data-ttu-id="f5dd6-127">Element rejestruje elementy podrzędne <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów sieciowych. `webRequestModules`</span><span class="sxs-lookup"><span data-stu-id="f5dd6-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="f5dd6-128">Moduły żądania sieci Web muszą implementować <xref:System.Net.IWebRequestCreate> interfejs.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="f5dd6-129">.NET Framework obejmuje moduły żądania sieci Web dla identyfikatorów URI zaczynających `http://`się `https://`od, `file://`i.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="f5dd6-130">Moduły domyślne można zastąpić tylko przez zarejestrowanie modułu niestandardowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f5dd6-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f5dd6-131">Configuration Files</span></span>  
 <span data-ttu-id="f5dd6-132">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f5dd6-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5dd6-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dd6-133">Example</span></span>  
 <span data-ttu-id="f5dd6-134">Poniższy przykład rejestruje domyślny moduł HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="f5dd6-135">Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="f5dd6-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5dd6-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5dd6-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="f5dd6-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f5dd6-137">Network Settings Schema</span></span>](index.md)
