---
title: <remove> Element dla authenticationModules (ustawienia sieci)
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
ms.openlocfilehash: 0eb3ef7db422d5cbbe70bd5633798b8d3787452d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125256"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ff33c-102">\<Usuń >, Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ff33c-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="ff33c-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff33c-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="ff33c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ff33c-104">\<configuration></span></span>  
<span data-ttu-id="ff33c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ff33c-105">\<system.net></span></span>  
<span data-ttu-id="ff33c-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="ff33c-106">\<authenticationModules></span></span>  
<span data-ttu-id="ff33c-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="ff33c-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff33c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff33c-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff33c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff33c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff33c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff33c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff33c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff33c-111">Attributes</span></span>  
  
|**<span data-ttu-id="ff33c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff33c-112">Attribute</span></span>**|**<span data-ttu-id="ff33c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ff33c-113">Description</span></span>**|  
|-------------------|---------------------|  
|**<span data-ttu-id="ff33c-114">— typ</span><span class="sxs-lookup"><span data-stu-id="ff33c-114">type</span></span>**|<span data-ttu-id="ff33c-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="ff33c-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff33c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff33c-116">Child Elements</span></span>  
 <span data-ttu-id="ff33c-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="ff33c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff33c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff33c-118">Parent Elements</span></span>  
  
|**<span data-ttu-id="ff33c-119">Element</span><span class="sxs-lookup"><span data-stu-id="ff33c-119">Element</span></span>**|**<span data-ttu-id="ff33c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ff33c-120">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="ff33c-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ff33c-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="ff33c-122">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="ff33c-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff33c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff33c-123">Remarks</span></span>  
 <span data-ttu-id="ff33c-124">`remove` Elementu usuwa moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff33c-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="ff33c-125">Wartość `type` atrybut powinien być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="ff33c-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ff33c-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ff33c-126">Configuration Files</span></span>  
 <span data-ttu-id="ff33c-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ff33c-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff33c-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff33c-128">Example</span></span>  
 <span data-ttu-id="ff33c-129">Poniższy przykład usuwa moduł usługi uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ff33c-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff33c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff33c-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ff33c-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ff33c-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
