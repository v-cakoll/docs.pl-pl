---
title: '&lt;webRequestModules —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7454099d8af0f2d656296be55677c648cc0c36c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="9003c-102">&lt;webRequestModules —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="9003c-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="9003c-103">Określa moduły służące do żądania informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="9003c-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="9003c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9003c-104">\<configuration></span></span>  
<span data-ttu-id="9003c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9003c-105">\<system.net></span></span>  
<span data-ttu-id="9003c-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="9003c-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9003c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9003c-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9003c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9003c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9003c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9003c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9003c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9003c-110">Attributes</span></span>  
 <span data-ttu-id="9003c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9003c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9003c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9003c-112">Child Elements</span></span>  
  
|<span data-ttu-id="9003c-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="9003c-113">**Element**</span></span>|<span data-ttu-id="9003c-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9003c-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9003c-115">add</span><span class="sxs-lookup"><span data-stu-id="9003c-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="9003c-116">Dodaje niestandardowego modułu żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9003c-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="9003c-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="9003c-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="9003c-118">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9003c-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="9003c-119">remove</span><span class="sxs-lookup"><span data-stu-id="9003c-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="9003c-120">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9003c-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9003c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9003c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9003c-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="9003c-122">**Element**</span></span>|<span data-ttu-id="9003c-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9003c-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9003c-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="9003c-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="9003c-125">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="9003c-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9003c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9003c-126">Remarks</span></span>  
 <span data-ttu-id="9003c-127">`webRequestModules` Element rejestruje elementów podrzędnych <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="9003c-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="9003c-128">Moduły żądania sieci Web musi implementować <xref:System.Net.IWebRequestCreate> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9003c-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="9003c-129">.NET Framework zawiera identyfikatory URI, które rozpoczynają się od http://, https:// i file:// modułów żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9003c-129">The .NET Framework includes Web request modules for URIs that begin with http://, https://, and file://.</span></span> <span data-ttu-id="9003c-130">Można zastąpić domyślne moduły tylko poprzez zarejestrowanie niestandardowego modułu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9003c-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9003c-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9003c-131">Configuration Files</span></span>  
 <span data-ttu-id="9003c-132">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9003c-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9003c-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9003c-133">Example</span></span>  
 <span data-ttu-id="9003c-134">Poniższy przykład rejestruje domyślny moduł HTTP.</span><span class="sxs-lookup"><span data-stu-id="9003c-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="9003c-135">Wartości należy zastąpić wersję i PublicKeyToken przy użyciu prawidłowych wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="9003c-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9003c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9003c-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="9003c-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9003c-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
