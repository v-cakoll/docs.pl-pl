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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087513"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d8670-102">\<clear>, element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="d8670-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="d8670-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8670-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="d8670-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8670-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8670-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d8670-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d8670-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d8670-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8670-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d8670-107">Attributes</span></span>  
 <span data-ttu-id="d8670-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="d8670-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8670-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d8670-109">Child Elements</span></span>  
 <span data-ttu-id="d8670-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d8670-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8670-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d8670-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d8670-112">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="d8670-112">**Element**</span></span>|<span data-ttu-id="d8670-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d8670-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8670-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d8670-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d8670-115">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="d8670-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8670-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8670-116">Remarks</span></span>  
 <span data-ttu-id="d8670-117">`clear`Element usuwa wszystkie moduły uwierzytelniania zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d8670-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d8670-118">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d8670-118">Configuration Files</span></span>  
 <span data-ttu-id="d8670-119">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d8670-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8670-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8670-120">Example</span></span>  
 <span data-ttu-id="d8670-121">Poniższy przykład usuwa wszystkie skonfigurowane moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="d8670-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8670-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8670-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d8670-123">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d8670-123">Network Settings Schema</span></span>](index.md)
