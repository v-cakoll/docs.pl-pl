---
title: '&lt;webRequestModules&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 4e2a37f6829341b33475f91796e8671d867ac151
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699795"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="5d3fe-102">&lt;webRequestModules&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="5d3fe-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5d3fe-103">Określa moduły do użycia na żądanie informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="5d3fe-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5d3fe-104">\<configuration></span></span>  
<span data-ttu-id="5d3fe-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5d3fe-105">\<system.net></span></span>  
<span data-ttu-id="5d3fe-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="5d3fe-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3fe-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d3fe-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d3fe-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d3fe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5d3fe-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d3fe-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d3fe-110">Attributes</span></span>  
 <span data-ttu-id="5d3fe-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d3fe-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d3fe-112">Child Elements</span></span>  
  
|<span data-ttu-id="5d3fe-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="5d3fe-113">**Element**</span></span>|<span data-ttu-id="5d3fe-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5d3fe-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5d3fe-115">add</span><span class="sxs-lookup"><span data-stu-id="5d3fe-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="5d3fe-116">Dodaje niestandardowy moduł żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="5d3fe-117">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="5d3fe-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="5d3fe-118">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="5d3fe-119">remove</span><span class="sxs-lookup"><span data-stu-id="5d3fe-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="5d3fe-120">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d3fe-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d3fe-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5d3fe-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="5d3fe-122">**Element**</span></span>|<span data-ttu-id="5d3fe-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5d3fe-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5d3fe-124">system.net</span><span class="sxs-lookup"><span data-stu-id="5d3fe-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="5d3fe-125">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d3fe-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d3fe-126">Remarks</span></span>  
 <span data-ttu-id="5d3fe-127">`webRequestModules` Element rejestruje podrzędne <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="5d3fe-128">Moduły żądania sieci Web musi implementować <xref:System.Net.IWebRequestCreate> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="5d3fe-129">Program .NET Framework zawiera moduły żądania sieci Web dla identyfikatorów URI, które zaczynają się od `http://`, `https://`, i `file://`.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="5d3fe-130">Można zastąpić domyślne moduły tylko poprzez zarejestrowanie niestandardowego modułu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5d3fe-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5d3fe-131">Configuration Files</span></span>  
 <span data-ttu-id="5d3fe-132">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5d3fe-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d3fe-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d3fe-133">Example</span></span>  
 <span data-ttu-id="5d3fe-134">Poniższy przykład rejestruje domyślny moduł HTTP.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="5d3fe-135">Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="5d3fe-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d3fe-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d3fe-136">See also</span></span>
- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="5d3fe-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="5d3fe-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
