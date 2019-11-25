---
title: <clear>, element dla authenticationModules (ustawienia sieci)
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
ms.openlocfilehash: e3abd1b4c76ebda885703ccf961d58657b582f19
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087513"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="cb754-102">\<Wyczyść element > dla authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cb754-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="cb754-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb754-103">Clears all authentication modules from the application.</span></span>  

<span data-ttu-id="cb754-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cb754-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb754-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cb754-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="cb754-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cb754-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="cb754-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="cb754-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cb754-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb754-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb754-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cb754-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cb754-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cb754-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb754-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cb754-111">Attributes</span></span>  
 <span data-ttu-id="cb754-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="cb754-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb754-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cb754-113">Child Elements</span></span>  
 <span data-ttu-id="cb754-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="cb754-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb754-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cb754-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cb754-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="cb754-116">**Element**</span></span>|<span data-ttu-id="cb754-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="cb754-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cb754-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="cb754-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="cb754-119">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="cb754-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb754-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb754-120">Remarks</span></span>  
 <span data-ttu-id="cb754-121">Element `clear` usuwa wszystkie moduły uwierzytelniania zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cb754-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cb754-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cb754-122">Configuration Files</span></span>  
 <span data-ttu-id="cb754-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="cb754-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb754-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb754-124">Example</span></span>  
 <span data-ttu-id="cb754-125">Poniższy przykład usuwa wszystkie skonfigurowane moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="cb754-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb754-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb754-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="cb754-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="cb754-127">Network Settings Schema</span></span>](index.md)
