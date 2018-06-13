---
title: '&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6843662b73f6b7d45dd12616f5118569a2d19975
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754509"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="6317d-102">&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="6317d-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6317d-103">Konfiguruje właściwości skryptu używana do wykrywania, serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6317d-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="6317d-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="6317d-104">\<configuration></span></span>  
<span data-ttu-id="6317d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6317d-105">\<system.net></span></span>  
<span data-ttu-id="6317d-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="6317d-106">\<settings></span></span>  
<span data-ttu-id="6317d-107">\<webproxyscript — ></span><span class="sxs-lookup"><span data-stu-id="6317d-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6317d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6317d-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6317d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6317d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6317d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6317d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6317d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6317d-111">Attributes</span></span>  
  
|<span data-ttu-id="6317d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6317d-112">Attribute</span></span>|<span data-ttu-id="6317d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6317d-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="6317d-114">Określa maksymalny czas, który można pobrać skryptu w godziny, minuty i sekundy.</span><span class="sxs-lookup"><span data-stu-id="6317d-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="6317d-115">Wartość domyślna to jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="6317d-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6317d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6317d-116">Child Elements</span></span>  
 <span data-ttu-id="6317d-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="6317d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6317d-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6317d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6317d-119">Element</span><span class="sxs-lookup"><span data-stu-id="6317d-119">Element</span></span>|<span data-ttu-id="6317d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6317d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6317d-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="6317d-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="6317d-122">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6317d-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6317d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6317d-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6317d-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6317d-124">Configuration Files</span></span>  
 <span data-ttu-id="6317d-125">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6317d-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6317d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6317d-126">See Also</span></span>  
 [<span data-ttu-id="6317d-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="6317d-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
