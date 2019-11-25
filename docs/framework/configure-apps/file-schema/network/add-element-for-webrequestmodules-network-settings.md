---
title: <add>, element dla webRequestModules (ustawienia sieci)
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
ms.openlocfilehash: 76dad0c0b75d20627e9f57fd1bb467bf17c9294c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088511"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="c7f10-102">\<dodać elementu > dla webRequestModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c7f10-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="c7f10-103">Dodaje niestandardowy moduł żądania sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7f10-103">Adds a custom Web request module to the application.</span></span>  

<span data-ttu-id="c7f10-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c7f10-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7f10-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c7f10-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c7f10-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c7f10-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="c7f10-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="c7f10-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c7f10-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7f10-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7f10-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7f10-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c7f10-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7f10-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7f10-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7f10-111">Attributes</span></span>  
  
|<span data-ttu-id="c7f10-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="c7f10-112">**Attribute**</span></span>|<span data-ttu-id="c7f10-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c7f10-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="c7f10-114">Prefiks identyfikatora URI dla żądań obsłużonych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c7f10-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="c7f10-115">W pełni kwalifikowana nazwa typu (wskazywana przez właściwość <xref:System.Type.FullName%2A>) i nazwa zestawu (wskazywanym przez właściwość <xref:System.Reflection.Assembly.FullName%2A>) oddzielone przecinkami, które implementują ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c7f10-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7f10-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7f10-116">Child Elements</span></span>  
 <span data-ttu-id="c7f10-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="c7f10-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7f10-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7f10-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c7f10-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="c7f10-119">**Element**</span></span>|<span data-ttu-id="c7f10-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c7f10-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c7f10-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="c7f10-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="c7f10-122">Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="c7f10-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7f10-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7f10-123">Remarks</span></span>  
 <span data-ttu-id="c7f10-124">Atrybut `prefix` definiuje prefiks identyfikatora URI, który używa określonego modułu żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c7f10-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="c7f10-125">Moduły żądania sieci Web są zwykle zarejestrowane w celu obsługi określonego protokołu, takiego jak HTTP lub FTP, ale mogą być zarejestrowane w celu obsługi żądania do określonego serwera lub ścieżki na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c7f10-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="c7f10-126">Moduł żądania sieci Web jest tworzony, gdy do metody <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> jest przesyłany prefiks pasujący do identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="c7f10-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c7f10-127">Wartość atrybutu `prefix` powinna być wiodącymi znakami prawidłowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="c7f10-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="c7f10-128">Na przykład `http` lub `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c7f10-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="c7f10-129">Wartość atrybutu `type` powinna być prawidłową nazwą typu i odpowiadającą jej nazwą zestawu, rozdzieloną przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c7f10-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="c7f10-130">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c7f10-130">Configuration Files</span></span>  
 <span data-ttu-id="c7f10-131">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c7f10-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7f10-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7f10-132">Example</span></span>  
 <span data-ttu-id="c7f10-133">Poniższy przykład rejestruje niestandardowy moduł żądania sieci Web dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7f10-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="c7f10-134">Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="c7f10-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7f10-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7f10-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="c7f10-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c7f10-136">Network Settings Schema</span></span>](index.md)
