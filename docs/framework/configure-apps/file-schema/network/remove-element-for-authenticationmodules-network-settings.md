---
title: "&lt;Usuń&gt; elementu authenticationModules — (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eb8490241d4ec8a34a76aa6087c1f4d27d5cebb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="9e757-102">&lt;Usuń&gt; elementu authenticationModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="9e757-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="9e757-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e757-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="9e757-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9e757-104">\<configuration></span></span>  
<span data-ttu-id="9e757-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="9e757-105">\<system.net></span></span>  
<span data-ttu-id="9e757-106">\<authenticationModules — ></span><span class="sxs-lookup"><span data-stu-id="9e757-106">\<authenticationModules></span></span>  
<span data-ttu-id="9e757-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="9e757-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e757-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e757-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e757-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e757-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9e757-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9e757-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e757-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e757-111">Attributes</span></span>  
  
|<span data-ttu-id="9e757-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="9e757-112">**Attribute**</span></span>|<span data-ttu-id="9e757-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9e757-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="9e757-114">**Typ**</span><span class="sxs-lookup"><span data-stu-id="9e757-114">**type**</span></span>|<span data-ttu-id="9e757-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="9e757-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e757-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e757-116">Child Elements</span></span>  
 <span data-ttu-id="9e757-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="9e757-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e757-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e757-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9e757-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="9e757-119">**Element**</span></span>|<span data-ttu-id="9e757-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9e757-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9e757-121">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="9e757-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="9e757-122">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="9e757-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e757-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e757-123">Remarks</span></span>  
 <span data-ttu-id="9e757-124">`remove` Element usuwa moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9e757-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="9e757-125">Wartość `type` atrybutu powinna być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="9e757-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9e757-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9e757-126">Configuration Files</span></span>  
 <span data-ttu-id="9e757-127">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9e757-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e757-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e757-128">Example</span></span>  
 <span data-ttu-id="9e757-129">Poniższy przykład umożliwia usunięcie moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9e757-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e757-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e757-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="9e757-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9e757-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
