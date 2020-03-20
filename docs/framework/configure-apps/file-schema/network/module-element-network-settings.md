---
title: <module>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154832"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="734e0-102">\<moduł> element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="734e0-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="734e0-103">Dodaje nowy moduł serwera proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="734e0-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="734e0-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="734e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="734e0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="734e0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="734e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="734e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="734e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>modułów**</span><span class="sxs-lookup"><span data-stu-id="734e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="734e0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="734e0-108">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="734e0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="734e0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="734e0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="734e0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="734e0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="734e0-111">Attributes</span></span>  
  
|<span data-ttu-id="734e0-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="734e0-112">**Attribute**</span></span>|<span data-ttu-id="734e0-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="734e0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="734e0-114">W pełni kwalifikowana nazwa typu <xref:System.Type.FullName%2A> (wskazana przez właściwość) <xref:System.Reflection.Assembly.FullName%2A> i nazwa zestawu (wskazana przez właściwość), oddzielona przecinkiem, która implementuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="734e0-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="734e0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="734e0-115">Child Elements</span></span>  
 <span data-ttu-id="734e0-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="734e0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="734e0-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="734e0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="734e0-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="734e0-118">**Element**</span></span>|<span data-ttu-id="734e0-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="734e0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="734e0-120">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="734e0-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="734e0-121">Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).</span><span class="sxs-lookup"><span data-stu-id="734e0-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="734e0-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="734e0-122">Remarks</span></span>  
 <span data-ttu-id="734e0-123">Element `module` rejestruje klasy proxy, <xref:System.Net.IWebProxy> które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="734e0-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="734e0-124">Po zarejestrowaniu klasy `module` proxy, może służyć do żądania informacji za pośrednictwem obsługiwanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="734e0-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="734e0-125">Wartość atrybutu `type` powinna być nazwą klasy modułu i nazwą odpowiadającej mu biblioteki dynamicznego łącza (DLL).</span><span class="sxs-lookup"><span data-stu-id="734e0-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="734e0-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="734e0-126">Configuration Files</span></span>  
 <span data-ttu-id="734e0-127">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="734e0-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="734e0-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="734e0-128">Example</span></span>  
 <span data-ttu-id="734e0-129">Poniższy przykład rejestruje niestandardową klasę serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="734e0-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="734e0-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="734e0-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="734e0-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="734e0-131">Network Settings Schema</span></span>](index.md)
