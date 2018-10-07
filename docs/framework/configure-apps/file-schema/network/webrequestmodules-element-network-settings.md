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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7cd25b980afa067ac78fc081c0a7a8e65a23258b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838263"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="37f8c-102">&lt;webRequestModules&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="37f8c-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="37f8c-103">Określa moduły do użycia na żądanie informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="37f8c-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="37f8c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="37f8c-104">\<configuration></span></span>  
<span data-ttu-id="37f8c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="37f8c-105">\<system.net></span></span>  
<span data-ttu-id="37f8c-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="37f8c-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f8c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="37f8c-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37f8c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37f8c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37f8c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37f8c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37f8c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37f8c-110">Attributes</span></span>  
 <span data-ttu-id="37f8c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="37f8c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37f8c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37f8c-112">Child Elements</span></span>  
  
|<span data-ttu-id="37f8c-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="37f8c-113">**Element**</span></span>|<span data-ttu-id="37f8c-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="37f8c-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="37f8c-115">add</span><span class="sxs-lookup"><span data-stu-id="37f8c-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="37f8c-116">Dodaje niestandardowy moduł żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37f8c-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="37f8c-117">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="37f8c-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="37f8c-118">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37f8c-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="37f8c-119">remove</span><span class="sxs-lookup"><span data-stu-id="37f8c-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="37f8c-120">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37f8c-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37f8c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37f8c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="37f8c-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="37f8c-122">**Element**</span></span>|<span data-ttu-id="37f8c-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="37f8c-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="37f8c-124">przestrzeni nazw System.NET</span><span class="sxs-lookup"><span data-stu-id="37f8c-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="37f8c-125">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="37f8c-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37f8c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37f8c-126">Remarks</span></span>  
 <span data-ttu-id="37f8c-127">`webRequestModules` Element rejestruje podrzędne <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="37f8c-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="37f8c-128">Moduły żądania sieci Web musi implementować <xref:System.Net.IWebRequestCreate> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="37f8c-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="37f8c-129">Program .NET Framework zawiera moduły żądania sieci Web dla identyfikatorów URI, które zaczynają się od `http://`, `https://`, i `file://`.</span><span class="sxs-lookup"><span data-stu-id="37f8c-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="37f8c-130">Można zastąpić domyślne moduły tylko poprzez zarejestrowanie niestandardowego modułu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37f8c-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="37f8c-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="37f8c-131">Configuration Files</span></span>  
 <span data-ttu-id="37f8c-132">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="37f8c-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37f8c-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="37f8c-133">Example</span></span>  
 <span data-ttu-id="37f8c-134">Poniższy przykład rejestruje domyślny moduł HTTP.</span><span class="sxs-lookup"><span data-stu-id="37f8c-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="37f8c-135">Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="37f8c-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37f8c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37f8c-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="37f8c-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="37f8c-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
