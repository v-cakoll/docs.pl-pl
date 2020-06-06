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
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154780"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="836f1-102">\<remove>, element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="836f1-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="836f1-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="836f1-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="836f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="836f1-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="836f1-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="836f1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="836f1-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="836f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="836f1-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="836f1-107">Attributes</span></span>  
  
|<span data-ttu-id="836f1-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="836f1-108">**Attribute**</span></span>|<span data-ttu-id="836f1-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="836f1-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="836f1-110">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="836f1-110">**type**</span></span>|<span data-ttu-id="836f1-111">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="836f1-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="836f1-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="836f1-112">Child Elements</span></span>  
 <span data-ttu-id="836f1-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="836f1-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="836f1-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="836f1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="836f1-115">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="836f1-115">**Element**</span></span>|<span data-ttu-id="836f1-116">**Opis**</span><span class="sxs-lookup"><span data-stu-id="836f1-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="836f1-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="836f1-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="836f1-118">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="836f1-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="836f1-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="836f1-119">Remarks</span></span>  
 <span data-ttu-id="836f1-120">`remove`Element usuwa moduły uwierzytelniania zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="836f1-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="836f1-121">Wartość `type` atrybutu powinna być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="836f1-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="836f1-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="836f1-122">Configuration Files</span></span>  
 <span data-ttu-id="836f1-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="836f1-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="836f1-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="836f1-124">Example</span></span>  
 <span data-ttu-id="836f1-125">Poniższy przykład usuwa moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="836f1-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="836f1-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="836f1-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="836f1-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="836f1-127">Network Settings Schema</span></span>](index.md)
