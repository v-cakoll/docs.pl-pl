---
title: "&lt;Wyczyść&gt; elementu authenticationModules — (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b1c27ba6cdae88a36813dcf67ffc386c94403c1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="9f9fd-102">&lt;Wyczyść&gt; elementu authenticationModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="9f9fd-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="9f9fd-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="9f9fd-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9f9fd-104">\<configuration></span></span>  
<span data-ttu-id="9f9fd-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="9f9fd-105">\<system.net></span></span>  
<span data-ttu-id="9f9fd-106">\<authenticationModules — ></span><span class="sxs-lookup"><span data-stu-id="9f9fd-106">\<authenticationModules></span></span>  
<span data-ttu-id="9f9fd-107">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="9f9fd-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9fd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f9fd-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f9fd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9f9fd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9f9fd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f9fd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f9fd-111">Attributes</span></span>  
 <span data-ttu-id="9f9fd-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f9fd-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f9fd-113">Child Elements</span></span>  
 <span data-ttu-id="9f9fd-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f9fd-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9f9fd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9f9fd-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="9f9fd-116">**Element**</span></span>|<span data-ttu-id="9f9fd-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9f9fd-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9f9fd-118">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="9f9fd-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="9f9fd-119">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9fd-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f9fd-120">Remarks</span></span>  
 <span data-ttu-id="9f9fd-121">`clear` Element usuwa wszystkie moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9f9fd-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9f9fd-122">Configuration Files</span></span>  
 <span data-ttu-id="9f9fd-123">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9f9fd-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9fd-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f9fd-124">Example</span></span>  
 <span data-ttu-id="9f9fd-125">Poniższy przykład umożliwia usunięcie wszystkich modułów skonfigurowanego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f9fd-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f9fd-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="9f9fd-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9f9fd-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
