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
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873271"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="fb496-102">&lt;Usuń&gt; Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="fb496-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="fb496-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb496-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="fb496-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="fb496-104">\<configuration></span></span>  
<span data-ttu-id="fb496-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fb496-105">\<system.net></span></span>  
<span data-ttu-id="fb496-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="fb496-106">\<authenticationModules></span></span>  
<span data-ttu-id="fb496-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="fb496-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb496-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb496-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb496-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb496-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fb496-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb496-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb496-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb496-111">Attributes</span></span>  
  
|<span data-ttu-id="fb496-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="fb496-112">**Attribute**</span></span>|<span data-ttu-id="fb496-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="fb496-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="fb496-114">**Typ**</span><span class="sxs-lookup"><span data-stu-id="fb496-114">**type**</span></span>|<span data-ttu-id="fb496-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fb496-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb496-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb496-116">Child Elements</span></span>  
 <span data-ttu-id="fb496-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb496-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb496-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb496-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fb496-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="fb496-119">**Element**</span></span>|<span data-ttu-id="fb496-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="fb496-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fb496-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="fb496-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="fb496-122">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="fb496-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb496-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb496-123">Remarks</span></span>  
 <span data-ttu-id="fb496-124">`remove` Elementu usuwa moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fb496-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="fb496-125">Wartość `type` atrybut powinien być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="fb496-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fb496-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fb496-126">Configuration Files</span></span>  
 <span data-ttu-id="fb496-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fb496-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb496-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb496-128">Example</span></span>  
 <span data-ttu-id="fb496-129">Poniższy przykład usuwa moduł usługi uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fb496-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb496-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb496-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="fb496-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="fb496-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
