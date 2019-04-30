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
ms.openlocfilehash: 3c018c7d474286f7a9cde2d070e4b54d164b5b40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674613"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d62f0-102">\<Wyczyść >, Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="d62f0-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="d62f0-103">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d62f0-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="d62f0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d62f0-104">\<configuration></span></span>  
<span data-ttu-id="d62f0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d62f0-105">\<system.net></span></span>  
<span data-ttu-id="d62f0-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="d62f0-106">\<authenticationModules></span></span>  
<span data-ttu-id="d62f0-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="d62f0-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d62f0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d62f0-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d62f0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d62f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d62f0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d62f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d62f0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d62f0-111">Attributes</span></span>  
 <span data-ttu-id="d62f0-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="d62f0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d62f0-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d62f0-113">Child Elements</span></span>  
 <span data-ttu-id="d62f0-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d62f0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d62f0-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d62f0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d62f0-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="d62f0-116">**Element**</span></span>|<span data-ttu-id="d62f0-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d62f0-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d62f0-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d62f0-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="d62f0-119">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="d62f0-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d62f0-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d62f0-120">Remarks</span></span>  
 <span data-ttu-id="d62f0-121">`clear` Elementu usuwa wszystkie moduły uwierzytelniania, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d62f0-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d62f0-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d62f0-122">Configuration Files</span></span>  
 <span data-ttu-id="d62f0-123">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d62f0-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d62f0-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="d62f0-124">Example</span></span>  
 <span data-ttu-id="d62f0-125">Poniższy przykład usuwa wszystkie moduły uwierzytelniania skonfigurowanego.</span><span class="sxs-lookup"><span data-stu-id="d62f0-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d62f0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d62f0-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d62f0-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d62f0-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
