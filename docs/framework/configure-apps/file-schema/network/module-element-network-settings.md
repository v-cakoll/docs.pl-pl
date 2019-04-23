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
ms.openlocfilehash: 0d108f2350d82666e3dc24f0f6854fe64ea4755f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084118"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="d56f0-102">\<Moduł >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="d56f0-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="d56f0-103">Dodaje nowy moduł serwera proxy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d56f0-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="d56f0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d56f0-104">\<configuration></span></span>  
<span data-ttu-id="d56f0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d56f0-105">\<system.net></span></span>  
<span data-ttu-id="d56f0-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="d56f0-106">\<defaultProxy></span></span>  
<span data-ttu-id="d56f0-107">\<module></span><span class="sxs-lookup"><span data-stu-id="d56f0-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56f0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d56f0-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d56f0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d56f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d56f0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d56f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d56f0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d56f0-111">Attributes</span></span>  
  
|<span data-ttu-id="d56f0-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="d56f0-112">**Attribute**</span></span>|<span data-ttu-id="d56f0-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d56f0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="d56f0-114">W pełni kwalifikowana nazwa typu (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), oddzielone przecinkami, który implementuje serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d56f0-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d56f0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d56f0-115">Child Elements</span></span>  
 <span data-ttu-id="d56f0-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="d56f0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d56f0-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d56f0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d56f0-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="d56f0-118">**Element**</span></span>|<span data-ttu-id="d56f0-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d56f0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d56f0-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d56f0-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="d56f0-121">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="d56f0-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d56f0-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d56f0-122">Remarks</span></span>  
 <span data-ttu-id="d56f0-123">`module` Element rejestruje klasy serwera proxy, które implementują <xref:System.Net.IWebProxy> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d56f0-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="d56f0-124">Po zarejestrowaniu klasy proxy `module` może służyć do żądania informacji za pośrednictwem obsługiwanych serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d56f0-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="d56f0-125">Wartość `type` atrybut powinien mieć nazwę klasy, modułu i nazwą z jej odpowiednie dynamiczne łącze biblioteki (DLL).</span><span class="sxs-lookup"><span data-stu-id="d56f0-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d56f0-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d56f0-126">Configuration Files</span></span>  
 <span data-ttu-id="d56f0-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d56f0-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d56f0-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d56f0-128">Example</span></span>  
 <span data-ttu-id="d56f0-129">Poniższy przykład rejestruje klasę niestandardowego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d56f0-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d56f0-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d56f0-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d56f0-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d56f0-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
