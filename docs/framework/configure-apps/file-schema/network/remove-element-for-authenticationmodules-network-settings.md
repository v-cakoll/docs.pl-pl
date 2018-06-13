---
title: '&lt;Usuń&gt; elementu authenticationModules — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a22ddbada0162ba38589b244cab9123f33d7cf45
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742393"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="477dc-102">&lt;Usuń&gt; elementu authenticationModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="477dc-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="477dc-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="477dc-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="477dc-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="477dc-104">\<configuration></span></span>  
<span data-ttu-id="477dc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="477dc-105">\<system.net></span></span>  
<span data-ttu-id="477dc-106">\<authenticationModules — ></span><span class="sxs-lookup"><span data-stu-id="477dc-106">\<authenticationModules></span></span>  
<span data-ttu-id="477dc-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="477dc-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="477dc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="477dc-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="477dc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="477dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="477dc-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="477dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="477dc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="477dc-111">Attributes</span></span>  
  
|<span data-ttu-id="477dc-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="477dc-112">**Attribute**</span></span>|<span data-ttu-id="477dc-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="477dc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="477dc-114">**Typ**</span><span class="sxs-lookup"><span data-stu-id="477dc-114">**type**</span></span>|<span data-ttu-id="477dc-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="477dc-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="477dc-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="477dc-116">Child Elements</span></span>  
 <span data-ttu-id="477dc-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="477dc-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="477dc-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="477dc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="477dc-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="477dc-119">**Element**</span></span>|<span data-ttu-id="477dc-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="477dc-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="477dc-121">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="477dc-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="477dc-122">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="477dc-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="477dc-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="477dc-123">Remarks</span></span>  
 <span data-ttu-id="477dc-124">`remove` Element usuwa moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="477dc-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="477dc-125">Wartość `type` atrybutu powinna być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="477dc-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="477dc-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="477dc-126">Configuration Files</span></span>  
 <span data-ttu-id="477dc-127">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="477dc-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="477dc-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="477dc-128">Example</span></span>  
 <span data-ttu-id="477dc-129">Poniższy przykład umożliwia usunięcie moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="477dc-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="477dc-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="477dc-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="477dc-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="477dc-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
