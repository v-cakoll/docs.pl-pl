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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154832"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="268ef-102">\<module>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="268ef-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="268ef-103">Dodaje nowy moduł proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="268ef-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="268ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="268ef-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="268ef-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="268ef-105">Attributes and Elements</span></span>  
 <span data-ttu-id="268ef-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="268ef-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="268ef-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="268ef-107">Attributes</span></span>  
  
|<span data-ttu-id="268ef-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="268ef-108">**Attribute**</span></span>|<span data-ttu-id="268ef-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="268ef-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="268ef-110">W pełni kwalifikowana nazwa typu (wskazywana przez <xref:System.Type.FullName%2A> Właściwość) i nazwa zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> Właściwość) oddzielone przecinkami, które implementują serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="268ef-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="268ef-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="268ef-111">Child Elements</span></span>  
 <span data-ttu-id="268ef-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="268ef-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="268ef-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="268ef-113">Parent Elements</span></span>  
  
|<span data-ttu-id="268ef-114">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="268ef-114">**Element**</span></span>|<span data-ttu-id="268ef-115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="268ef-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="268ef-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="268ef-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="268ef-117">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="268ef-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="268ef-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="268ef-118">Remarks</span></span>  
 <span data-ttu-id="268ef-119">`module`Element rejestruje klasy proxy, które implementują <xref:System.Net.IWebProxy> interfejs.</span><span class="sxs-lookup"><span data-stu-id="268ef-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="268ef-120">Po zarejestrowaniu klasy proxy `module` może służyć do żądania informacji za pomocą obsługiwanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="268ef-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="268ef-121">Wartość `type` atrybutu powinna być nazwą klasy modułu i nazwą odpowiadającą jej biblioteką dołączaną dynamicznie (dll).</span><span class="sxs-lookup"><span data-stu-id="268ef-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="268ef-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="268ef-122">Configuration Files</span></span>  
 <span data-ttu-id="268ef-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="268ef-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="268ef-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="268ef-124">Example</span></span>  
 <span data-ttu-id="268ef-125">Poniższy przykład rejestruje niestandardową klasę proxy.</span><span class="sxs-lookup"><span data-stu-id="268ef-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="268ef-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="268ef-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="268ef-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="268ef-127">Network Settings Schema</span></span>](index.md)
