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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089060"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="912d8-102">\<webProxyScript>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="912d8-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="912d8-103">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="912d8-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="912d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="912d8-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="912d8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="912d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="912d8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="912d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="912d8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="912d8-107">Attributes</span></span>  
  
|<span data-ttu-id="912d8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="912d8-108">Attribute</span></span>|<span data-ttu-id="912d8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="912d8-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="912d8-110">Określa maksymalny czas pobierania skryptu w godzinach, minutach i sekundach.</span><span class="sxs-lookup"><span data-stu-id="912d8-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="912d8-111">Wartość domyślna to minutę.</span><span class="sxs-lookup"><span data-stu-id="912d8-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="912d8-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="912d8-112">Child Elements</span></span>  
 <span data-ttu-id="912d8-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="912d8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="912d8-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="912d8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="912d8-115">Element</span><span class="sxs-lookup"><span data-stu-id="912d8-115">Element</span></span>|<span data-ttu-id="912d8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="912d8-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="912d8-117">ustawienia</span><span class="sxs-lookup"><span data-stu-id="912d8-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="912d8-118">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="912d8-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="912d8-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="912d8-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="912d8-120">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="912d8-120">Configuration Files</span></span>  
 <span data-ttu-id="912d8-121">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="912d8-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912d8-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="912d8-122">See also</span></span>

- [<span data-ttu-id="912d8-123">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="912d8-123">Network Settings Schema</span></span>](index.md)
