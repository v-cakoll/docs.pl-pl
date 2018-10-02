---
title: '&lt;Dodaj&gt; Element dla webRequestModules (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 64df186be7d9e503ac22e177bca8da31e165f240
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032598"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="b364d-102">&lt;Dodaj&gt; Element dla webRequestModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="b364d-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="b364d-103">Dodaje niestandardowy moduł żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b364d-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="b364d-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b364d-104">\<configuration></span></span>  
<span data-ttu-id="b364d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b364d-105">\<system.net></span></span>  
<span data-ttu-id="b364d-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="b364d-106">\<webRequestModules></span></span>  
<span data-ttu-id="b364d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b364d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b364d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b364d-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b364d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b364d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b364d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b364d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b364d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b364d-111">Attributes</span></span>  
  
|<span data-ttu-id="b364d-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="b364d-112">**Attribute**</span></span>|<span data-ttu-id="b364d-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b364d-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="b364d-114">Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b364d-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="b364d-115">W pełni kwalifikowana nazwa typu (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), oddzielone przecinkami, który implementuje ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b364d-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b364d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b364d-116">Child Elements</span></span>  
 <span data-ttu-id="b364d-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="b364d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b364d-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b364d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b364d-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="b364d-119">**Element**</span></span>|<span data-ttu-id="b364d-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b364d-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b364d-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="b364d-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="b364d-122">Określa moduły do użycia na żądanie informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="b364d-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b364d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b364d-123">Remarks</span></span>  
 <span data-ttu-id="b364d-124">`prefix` Atrybut definiuje prefiks identyfikatora URI, który używa określonego modułu żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b364d-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="b364d-125">Moduły żądania sieci Web zwykle są rejestrowane do obsługi określonego protokołu, na przykład HTTP lub FTP, ale można zarejestrować do obsługi żądań do określonego serwera lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b364d-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="b364d-126">Moduł żądania sieci Web jest tworzony podczas dopasowywania prefiks identyfikatora URI jest przekazywany do <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b364d-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b364d-127">Wartość `prefix` atrybut powinien być wiodące znaki prawidłowym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="b364d-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="b364d-128">Na przykład `http` lub `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="b364d-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="b364d-129">Wartość `type` atrybut powinien być prawidłową nazwą typu i odpowiedniej nazwy zestawu, oddzielając wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b364d-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="b364d-130">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b364d-130">Configuration Files</span></span>  
 <span data-ttu-id="b364d-131">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b364d-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b364d-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b364d-132">Example</span></span>  
 <span data-ttu-id="b364d-133">Poniższy przykład rejestruje niestandardowego modułu żądania sieci Web do obsługi protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b364d-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="b364d-134">Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="b364d-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b364d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b364d-135">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="b364d-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b364d-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
