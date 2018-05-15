---
title: '&lt;Moduł&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 06c653d8759224e1112183a7e86e9797a97402af
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="b4a46-102">&lt;Moduł&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="b4a46-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b4a46-103">Dodaje nowy moduł serwera proxy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4a46-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="b4a46-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b4a46-104">\<configuration></span></span>  
<span data-ttu-id="b4a46-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b4a46-105">\<system.net></span></span>  
<span data-ttu-id="b4a46-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="b4a46-106">\<defaultProxy></span></span>  
<span data-ttu-id="b4a46-107">\<Moduł ></span><span class="sxs-lookup"><span data-stu-id="b4a46-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a46-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4a46-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4a46-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b4a46-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b4a46-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b4a46-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4a46-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b4a46-111">Attributes</span></span>  
  
|<span data-ttu-id="b4a46-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="b4a46-112">**Attribute**</span></span>|<span data-ttu-id="b4a46-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b4a46-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="b4a46-114">Nazwa typu w pełni kwalifikowaną (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), rozdzielone przecinkami, który implementuje serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b4a46-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4a46-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b4a46-115">Child Elements</span></span>  
 <span data-ttu-id="b4a46-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="b4a46-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4a46-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b4a46-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b4a46-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="b4a46-118">**Element**</span></span>|<span data-ttu-id="b4a46-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b4a46-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b4a46-120">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="b4a46-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="b4a46-121">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="b4a46-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4a46-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4a46-122">Remarks</span></span>  
 <span data-ttu-id="b4a46-123">`module` Element rejestruje klasy serwera proxy, które implementują <xref:System.Net.IWebProxy> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b4a46-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="b4a46-124">Po zarejestrowaniu klasy serwera proxy `module` mogą być używane do żądania informacji za pośrednictwem obsługiwanych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b4a46-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="b4a46-125">Wartość `type` atrybut powinien mieć nazwę klasy modułu i nazwą z jej odpowiednie dynamiczne łącze biblioteki (DLL).</span><span class="sxs-lookup"><span data-stu-id="b4a46-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b4a46-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b4a46-126">Configuration Files</span></span>  
 <span data-ttu-id="b4a46-127">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b4a46-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4a46-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4a46-128">Example</span></span>  
 <span data-ttu-id="b4a46-129">Poniższy przykład rejestruje klasę niestandardowego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b4a46-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4a46-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4a46-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="b4a46-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b4a46-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
