---
title: <remove> — Element dla authenticationModules (Ustawienia sieci)
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
ms.openlocfilehash: a8afdf442f8dc4e57a407583ea6c452330dae53f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281024"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="139d1-102">\<Usuń >, Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="139d1-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="139d1-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="139d1-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="139d1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="139d1-104">\<configuration></span></span>  
<span data-ttu-id="139d1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="139d1-105">\<system.net></span></span>  
<span data-ttu-id="139d1-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="139d1-106">\<authenticationModules></span></span>  
<span data-ttu-id="139d1-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="139d1-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="139d1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="139d1-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="139d1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="139d1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="139d1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="139d1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="139d1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="139d1-111">Attributes</span></span>  
  
|<span data-ttu-id="139d1-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="139d1-112">**Attribute**</span></span>|<span data-ttu-id="139d1-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="139d1-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="139d1-114">**type**</span><span class="sxs-lookup"><span data-stu-id="139d1-114">**type**</span></span>|<span data-ttu-id="139d1-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="139d1-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="139d1-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="139d1-116">Child Elements</span></span>  
 <span data-ttu-id="139d1-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="139d1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="139d1-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="139d1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="139d1-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="139d1-119">**Element**</span></span>|<span data-ttu-id="139d1-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="139d1-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="139d1-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="139d1-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="139d1-122">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="139d1-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="139d1-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="139d1-123">Remarks</span></span>  
 <span data-ttu-id="139d1-124">`remove` Elementu usuwa moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="139d1-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="139d1-125">Wartość `type` atrybut powinien być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="139d1-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="139d1-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="139d1-126">Configuration Files</span></span>  
 <span data-ttu-id="139d1-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="139d1-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="139d1-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="139d1-128">Example</span></span>  
 <span data-ttu-id="139d1-129">Poniższy przykład usuwa moduł usługi uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="139d1-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="139d1-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="139d1-130">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="139d1-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="139d1-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
