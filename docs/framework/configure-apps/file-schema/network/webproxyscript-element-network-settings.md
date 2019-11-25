---
title: <webProxyScript>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: dbad888cd0537f63c09840ac1053f924db9ea9bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089060"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="e8b12-102">\<element > webProxyScript (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e8b12-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="e8b12-103">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e8b12-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

<span data-ttu-id="e8b12-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e8b12-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e8b12-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e8b12-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e8b12-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](settings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="e8b12-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="e8b12-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="e8b12-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e8b12-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8b12-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8b12-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8b12-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8b12-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8b12-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8b12-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8b12-111">Attributes</span></span>  
  
|<span data-ttu-id="e8b12-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8b12-112">Attribute</span></span>|<span data-ttu-id="e8b12-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b12-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="e8b12-114">Określa maksymalny czas pobierania skryptu w godzinach, minutach i sekundach.</span><span class="sxs-lookup"><span data-stu-id="e8b12-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="e8b12-115">Wartość domyślna to minutę.</span><span class="sxs-lookup"><span data-stu-id="e8b12-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8b12-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8b12-116">Child Elements</span></span>  
 <span data-ttu-id="e8b12-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="e8b12-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8b12-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8b12-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e8b12-119">Element</span><span class="sxs-lookup"><span data-stu-id="e8b12-119">Element</span></span>|<span data-ttu-id="e8b12-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b12-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8b12-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="e8b12-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e8b12-122">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="e8b12-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8b12-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8b12-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e8b12-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8b12-124">Configuration Files</span></span>  
 <span data-ttu-id="e8b12-125">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e8b12-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b12-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8b12-126">See also</span></span>

- [<span data-ttu-id="e8b12-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e8b12-127">Network Settings Schema</span></span>](index.md)
