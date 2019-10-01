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
ms.openlocfilehash: 2abab3de2965c31c11d9acaf7b78f3a668563506
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697453"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="710a3-102">\<webProxyScript >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="710a3-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="710a3-103">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="710a3-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
[<span data-ttu-id="710a3-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="710a3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="710a3-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="710a3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="710a3-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="710a3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="710a3-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="710a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="710a3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="710a3-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="710a3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="710a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="710a3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="710a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="710a3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="710a3-111">Attributes</span></span>  
  
|<span data-ttu-id="710a3-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="710a3-112">Attribute</span></span>|<span data-ttu-id="710a3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="710a3-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="710a3-114">Określa maksymalny czas pobierania skryptu w godzinach, minutach i sekundach.</span><span class="sxs-lookup"><span data-stu-id="710a3-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="710a3-115">Wartość domyślna to minutę.</span><span class="sxs-lookup"><span data-stu-id="710a3-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="710a3-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="710a3-116">Child Elements</span></span>  
 <span data-ttu-id="710a3-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="710a3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="710a3-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="710a3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="710a3-119">Element</span><span class="sxs-lookup"><span data-stu-id="710a3-119">Element</span></span>|<span data-ttu-id="710a3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="710a3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="710a3-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="710a3-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="710a3-122">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="710a3-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="710a3-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="710a3-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="710a3-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="710a3-124">Configuration Files</span></span>  
 <span data-ttu-id="710a3-125">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="710a3-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="710a3-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="710a3-126">See also</span></span>

- [<span data-ttu-id="710a3-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="710a3-127">Network Settings Schema</span></span>](index.md)
