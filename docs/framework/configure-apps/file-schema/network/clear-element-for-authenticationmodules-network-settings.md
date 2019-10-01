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
ms.openlocfilehash: 052f7eef30500d37389585956728250a46b718a3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698398"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="2b43e-102">\<clear > elementu authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="2b43e-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="2b43e-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2b43e-103">Clears all authentication modules from the application.</span></span>  
  
[<span data-ttu-id="2b43e-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="2b43e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2b43e-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2b43e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="2b43e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2b43e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="2b43e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="2b43e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b43e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b43e-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b43e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b43e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2b43e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2b43e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b43e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b43e-111">Attributes</span></span>  
 <span data-ttu-id="2b43e-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b43e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b43e-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b43e-113">Child Elements</span></span>  
 <span data-ttu-id="2b43e-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b43e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b43e-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b43e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2b43e-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="2b43e-116">**Element**</span></span>|<span data-ttu-id="2b43e-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2b43e-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2b43e-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="2b43e-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="2b43e-119">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="2b43e-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b43e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b43e-120">Remarks</span></span>  
 <span data-ttu-id="2b43e-121">Element `clear` usuwa wszystkie moduły uwierzytelniania zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2b43e-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2b43e-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2b43e-122">Configuration Files</span></span>  
 <span data-ttu-id="2b43e-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2b43e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b43e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b43e-124">Example</span></span>  
 <span data-ttu-id="2b43e-125">Poniższy przykład usuwa wszystkie skonfigurowane moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="2b43e-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b43e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b43e-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="2b43e-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2b43e-127">Network Settings Schema</span></span>](index.md)
