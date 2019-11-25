---
title: <remove>, element dla authenticationModules (ustawienia sieci)
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
ms.openlocfilehash: 2113b2b81ae347b398b0f25028dc6c361aec8447
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089181"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="a81e3-102">\<usunąć elementu > dla authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a81e3-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="a81e3-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a81e3-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="a81e3-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a81e3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a81e3-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a81e3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="a81e3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a81e3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="a81e3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="a81e3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a81e3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a81e3-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a81e3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a81e3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a81e3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a81e3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a81e3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a81e3-111">Attributes</span></span>  
  
|<span data-ttu-id="a81e3-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="a81e3-112">**Attribute**</span></span>|<span data-ttu-id="a81e3-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a81e3-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="a81e3-114">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="a81e3-114">**type**</span></span>|<span data-ttu-id="a81e3-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="a81e3-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a81e3-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a81e3-116">Child Elements</span></span>  
 <span data-ttu-id="a81e3-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a81e3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a81e3-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a81e3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a81e3-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="a81e3-119">**Element**</span></span>|<span data-ttu-id="a81e3-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a81e3-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a81e3-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a81e3-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="a81e3-122">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="a81e3-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a81e3-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a81e3-123">Remarks</span></span>  
 <span data-ttu-id="a81e3-124">Element `remove` usuwa moduły uwierzytelniania zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a81e3-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="a81e3-125">Wartość atrybutu `type` powinna być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="a81e3-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a81e3-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a81e3-126">Configuration Files</span></span>  
 <span data-ttu-id="a81e3-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a81e3-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81e3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="a81e3-128">Example</span></span>  
 <span data-ttu-id="a81e3-129">Poniższy przykład usuwa moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a81e3-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a81e3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a81e3-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="a81e3-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a81e3-131">Network Settings Schema</span></span>](index.md)
