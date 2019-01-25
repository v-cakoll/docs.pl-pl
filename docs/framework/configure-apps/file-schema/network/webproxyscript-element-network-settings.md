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
ms.openlocfilehash: 580fcb17c16c4f5de137b8aa298db68c44867c52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536272"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="ae7a7-102">&lt;webproxyscript —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ae7a7-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="ae7a7-103">Konfiguruje właściwości skryptu używanej do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ae7a7-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="ae7a7-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ae7a7-104">\<configuration></span></span>  
<span data-ttu-id="ae7a7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ae7a7-105">\<system.net></span></span>  
<span data-ttu-id="ae7a7-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="ae7a7-106">\<settings></span></span>  
<span data-ttu-id="ae7a7-107">\<webProxyScript></span><span class="sxs-lookup"><span data-stu-id="ae7a7-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7a7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae7a7-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae7a7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ae7a7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ae7a7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ae7a7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae7a7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ae7a7-111">Attributes</span></span>  
  
|<span data-ttu-id="ae7a7-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ae7a7-112">Attribute</span></span>|<span data-ttu-id="ae7a7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ae7a7-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="ae7a7-114">Określa maksymalny czas, aby pobrać skrypt w godzinach, minutach i sekundach.</span><span class="sxs-lookup"><span data-stu-id="ae7a7-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="ae7a7-115">Wartość domyślna to jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="ae7a7-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae7a7-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ae7a7-116">Child Elements</span></span>  
 <span data-ttu-id="ae7a7-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="ae7a7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae7a7-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ae7a7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ae7a7-119">Element</span><span class="sxs-lookup"><span data-stu-id="ae7a7-119">Element</span></span>|<span data-ttu-id="ae7a7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ae7a7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae7a7-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="ae7a7-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="ae7a7-122">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ae7a7-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae7a7-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae7a7-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ae7a7-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ae7a7-124">Configuration Files</span></span>  
 <span data-ttu-id="ae7a7-125">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ae7a7-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7a7-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae7a7-126">See also</span></span>
- [<span data-ttu-id="ae7a7-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ae7a7-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
