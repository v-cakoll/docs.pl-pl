---
title: "&lt;Moduł&gt; elementu (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a039f6ed985997c5557659abd299fe0fc7699a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="7a191-102">&lt;Moduł&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="7a191-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="7a191-103">Dodaje nowy moduł serwera proxy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a191-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="7a191-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7a191-104">\<configuration></span></span>  
<span data-ttu-id="7a191-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="7a191-105">\<system.net></span></span>  
<span data-ttu-id="7a191-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="7a191-106">\<defaultProxy></span></span>  
<span data-ttu-id="7a191-107">\<Moduł ></span><span class="sxs-lookup"><span data-stu-id="7a191-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a191-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a191-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a191-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a191-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7a191-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a191-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a191-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a191-111">Attributes</span></span>  
  
|<span data-ttu-id="7a191-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="7a191-112">**Attribute**</span></span>|<span data-ttu-id="7a191-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="7a191-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="7a191-114">Nazwa typu w pełni kwalifikowaną (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), rozdzielone przecinkami, który implementuje serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="7a191-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a191-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a191-115">Child Elements</span></span>  
 <span data-ttu-id="7a191-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7a191-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a191-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a191-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7a191-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="7a191-118">**Element**</span></span>|<span data-ttu-id="7a191-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="7a191-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7a191-120">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="7a191-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="7a191-121">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="7a191-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a191-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a191-122">Remarks</span></span>  
 <span data-ttu-id="7a191-123">`module` Element rejestruje klasy serwera proxy, które implementują <xref:System.Net.IWebProxy> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7a191-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="7a191-124">Po zarejestrowaniu klasy serwera proxy `module` mogą być używane do żądania informacji za pośrednictwem obsługiwanych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="7a191-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="7a191-125">Wartość `type` atrybut powinien mieć nazwę klasy modułu i nazwą z jej odpowiednie dynamiczne łącze biblioteki (DLL).</span><span class="sxs-lookup"><span data-stu-id="7a191-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7a191-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7a191-126">Configuration Files</span></span>  
 <span data-ttu-id="7a191-127">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7a191-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a191-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a191-128">Example</span></span>  
 <span data-ttu-id="7a191-129">Poniższy przykład rejestruje klasę niestandardowego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="7a191-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a191-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a191-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="7a191-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="7a191-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
