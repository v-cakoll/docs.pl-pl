---
title: '&lt;Usuń&gt; Element dla authenticationModules (ustawienia sieci)'
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
ms.openlocfilehash: 332f8eb4fb1a5a02df76c5745522037b029a2407
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072797"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="4cdd6-102">&lt;Usuń&gt; Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4cdd6-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="4cdd6-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="4cdd6-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4cdd6-104">\<configuration></span></span>  
<span data-ttu-id="4cdd6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4cdd6-105">\<system.net></span></span>  
<span data-ttu-id="4cdd6-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="4cdd6-106">\<authenticationModules></span></span>  
<span data-ttu-id="4cdd6-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="4cdd6-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdd6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cdd6-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cdd6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4cdd6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4cdd6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cdd6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4cdd6-111">Attributes</span></span>  
  
|<span data-ttu-id="4cdd6-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="4cdd6-112">**Attribute**</span></span>|<span data-ttu-id="4cdd6-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4cdd6-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="4cdd6-114">**Typ**</span><span class="sxs-lookup"><span data-stu-id="4cdd6-114">**type**</span></span>|<span data-ttu-id="4cdd6-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cdd6-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4cdd6-116">Child Elements</span></span>  
 <span data-ttu-id="4cdd6-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cdd6-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4cdd6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4cdd6-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="4cdd6-119">**Element**</span></span>|<span data-ttu-id="4cdd6-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4cdd6-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4cdd6-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="4cdd6-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="4cdd6-122">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cdd6-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cdd6-123">Remarks</span></span>  
 <span data-ttu-id="4cdd6-124">`remove` Elementu usuwa moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="4cdd6-125">Wartość `type` atrybut powinien być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4cdd6-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4cdd6-126">Configuration Files</span></span>  
 <span data-ttu-id="4cdd6-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4cdd6-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdd6-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="4cdd6-128">Example</span></span>  
 <span data-ttu-id="4cdd6-129">Poniższy przykład usuwa moduł usługi uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4cdd6-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cdd6-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cdd6-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="4cdd6-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="4cdd6-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
