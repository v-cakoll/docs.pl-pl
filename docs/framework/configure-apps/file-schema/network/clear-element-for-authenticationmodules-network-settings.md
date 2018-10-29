---
title: '&lt;Wyczyść&gt; Element dla authenticationModules (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: 42fa6a44891e012300f61f1a11a47537c6739e2c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205194"
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="76e90-102">&lt;Wyczyść&gt; Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="76e90-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="76e90-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="76e90-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="76e90-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="76e90-104">\<configuration></span></span>  
<span data-ttu-id="76e90-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="76e90-105">\<system.net></span></span>  
<span data-ttu-id="76e90-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="76e90-106">\<authenticationModules></span></span>  
<span data-ttu-id="76e90-107">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="76e90-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e90-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="76e90-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76e90-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="76e90-109">Attributes and Elements</span></span>  
 <span data-ttu-id="76e90-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="76e90-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76e90-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="76e90-111">Attributes</span></span>  
 <span data-ttu-id="76e90-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="76e90-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76e90-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="76e90-113">Child Elements</span></span>  
 <span data-ttu-id="76e90-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="76e90-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76e90-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="76e90-115">Parent Elements</span></span>  
  
|<span data-ttu-id="76e90-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="76e90-116">**Element**</span></span>|<span data-ttu-id="76e90-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="76e90-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="76e90-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="76e90-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="76e90-119">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="76e90-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76e90-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76e90-120">Remarks</span></span>  
 <span data-ttu-id="76e90-121">`clear` Elementu usuwa wszystkie moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="76e90-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="76e90-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="76e90-122">Configuration Files</span></span>  
 <span data-ttu-id="76e90-123">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="76e90-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76e90-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="76e90-124">Example</span></span>  
 <span data-ttu-id="76e90-125">Poniższy przykład usuwa wszystkie moduły uwierzytelniania skonfigurowanego.</span><span class="sxs-lookup"><span data-stu-id="76e90-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76e90-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76e90-126">See Also</span></span>  
- <xref:System.Net.IAuthenticationModule>  
- <xref:System.Net.AuthenticationManager>  
- [<span data-ttu-id="76e90-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="76e90-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
