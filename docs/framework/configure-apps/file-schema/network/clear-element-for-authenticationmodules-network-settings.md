---
title: '&lt;Wyczyść&gt; elementu authenticationModules — (ustawienia sieciowe)'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 94e0242ca685e8b0118a55ba44fb0569c13f10f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="58539-102">&lt;Wyczyść&gt; elementu authenticationModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="58539-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="58539-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58539-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="58539-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="58539-104">\<configuration></span></span>  
<span data-ttu-id="58539-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="58539-105">\<system.net></span></span>  
<span data-ttu-id="58539-106">\<authenticationModules — ></span><span class="sxs-lookup"><span data-stu-id="58539-106">\<authenticationModules></span></span>  
<span data-ttu-id="58539-107">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="58539-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58539-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="58539-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58539-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="58539-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58539-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="58539-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58539-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="58539-111">Attributes</span></span>  
 <span data-ttu-id="58539-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="58539-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58539-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="58539-113">Child Elements</span></span>  
 <span data-ttu-id="58539-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="58539-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58539-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="58539-115">Parent Elements</span></span>  
  
|<span data-ttu-id="58539-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="58539-116">**Element**</span></span>|<span data-ttu-id="58539-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="58539-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="58539-118">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="58539-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="58539-119">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="58539-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58539-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58539-120">Remarks</span></span>  
 <span data-ttu-id="58539-121">`clear` Element usuwa wszystkie moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="58539-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="58539-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="58539-122">Configuration Files</span></span>  
 <span data-ttu-id="58539-123">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="58539-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58539-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="58539-124">Example</span></span>  
 <span data-ttu-id="58539-125">Poniższy przykład umożliwia usunięcie wszystkich modułów skonfigurowanego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="58539-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58539-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58539-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="58539-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="58539-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
