---
title: '&lt;webproxyscript —&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 683c4c5e3f3f62d947ce244c66cc590eabe64f17
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195791"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="c592b-102">&lt;webproxyscript —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c592b-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c592b-103">Konfiguruje właściwości skryptu używanej do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c592b-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="c592b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c592b-104">\<configuration></span></span>  
<span data-ttu-id="c592b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c592b-105">\<system.net></span></span>  
<span data-ttu-id="c592b-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="c592b-106">\<settings></span></span>  
<span data-ttu-id="c592b-107">\<webproxyscript — ></span><span class="sxs-lookup"><span data-stu-id="c592b-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c592b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c592b-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c592b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c592b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c592b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c592b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c592b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c592b-111">Attributes</span></span>  
  
|<span data-ttu-id="c592b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c592b-112">Attribute</span></span>|<span data-ttu-id="c592b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c592b-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="c592b-114">Określa maksymalny czas, aby pobrać skrypt w godzinach, minutach i sekundach.</span><span class="sxs-lookup"><span data-stu-id="c592b-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="c592b-115">Wartość domyślna to jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="c592b-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c592b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c592b-116">Child Elements</span></span>  
 <span data-ttu-id="c592b-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="c592b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c592b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c592b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c592b-119">Element</span><span class="sxs-lookup"><span data-stu-id="c592b-119">Element</span></span>|<span data-ttu-id="c592b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c592b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c592b-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="c592b-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="c592b-122">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c592b-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c592b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c592b-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c592b-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c592b-124">Configuration Files</span></span>  
 <span data-ttu-id="c592b-125">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c592b-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c592b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c592b-126">See Also</span></span>  
- [<span data-ttu-id="c592b-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c592b-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
