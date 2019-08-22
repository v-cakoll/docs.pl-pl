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
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664066"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="7c5ed-102">\<module > element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="7c5ed-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="7c5ed-103">Dodaje nowy moduł proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7c5ed-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="7c5ed-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c5ed-104">\<configuration></span></span>  
<span data-ttu-id="7c5ed-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="7c5ed-105">\<system.net></span></span>  
<span data-ttu-id="7c5ed-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="7c5ed-106">\<defaultProxy></span></span>  
<span data-ttu-id="7c5ed-107">\<> modułu</span><span class="sxs-lookup"><span data-stu-id="7c5ed-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c5ed-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c5ed-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c5ed-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c5ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7c5ed-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c5ed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c5ed-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c5ed-111">Attributes</span></span>  
  
|<span data-ttu-id="7c5ed-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="7c5ed-112">**Attribute**</span></span>|<span data-ttu-id="7c5ed-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="7c5ed-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="7c5ed-114">W pełni kwalifikowana nazwa typu (wskazywana przez <xref:System.Type.FullName%2A> Właściwość) i nazwa zestawu (wskazywanym <xref:System.Reflection.Assembly.FullName%2A> przez właściwość) oddzielone przecinkami, które implementują serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="7c5ed-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c5ed-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c5ed-115">Child Elements</span></span>  
 <span data-ttu-id="7c5ed-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7c5ed-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c5ed-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c5ed-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7c5ed-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="7c5ed-118">**Element**</span></span>|<span data-ttu-id="7c5ed-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="7c5ed-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7c5ed-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="7c5ed-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="7c5ed-121">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="7c5ed-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c5ed-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c5ed-122">Remarks</span></span>  
 <span data-ttu-id="7c5ed-123">Element rejestruje klasy proxy, które <xref:System.Net.IWebProxy> implementują interfejs. `module`</span><span class="sxs-lookup"><span data-stu-id="7c5ed-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="7c5ed-124">Po zarejestrowaniu klasy `module` proxy może służyć do żądania informacji za pomocą obsługiwanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="7c5ed-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="7c5ed-125">Wartość `type` atrybutu powinna być nazwą klasy modułu i nazwą odpowiadającą jej biblioteką dołączaną dynamicznie (dll).</span><span class="sxs-lookup"><span data-stu-id="7c5ed-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7c5ed-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c5ed-126">Configuration Files</span></span>  
 <span data-ttu-id="7c5ed-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="7c5ed-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c5ed-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c5ed-128">Example</span></span>  
 <span data-ttu-id="7c5ed-129">Poniższy przykład rejestruje niestandardową klasę proxy.</span><span class="sxs-lookup"><span data-stu-id="7c5ed-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c5ed-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c5ed-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="7c5ed-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="7c5ed-131">Network Settings Schema</span></span>](index.md)
