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
ms.openlocfilehash: 7f923ce73760fa42a2c435d346f9d1097a5ed82f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664051"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="2cbfe-102">\<Usuń element > dla authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="2cbfe-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="2cbfe-103">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="2cbfe-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2cbfe-104">\<configuration></span></span>  
<span data-ttu-id="2cbfe-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2cbfe-105">\<system.net></span></span>  
<span data-ttu-id="2cbfe-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="2cbfe-106">\<authenticationModules></span></span>  
<span data-ttu-id="2cbfe-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="2cbfe-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbfe-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cbfe-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cbfe-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2cbfe-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2cbfe-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cbfe-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2cbfe-111">Attributes</span></span>  
  
|<span data-ttu-id="2cbfe-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="2cbfe-112">**Attribute**</span></span>|<span data-ttu-id="2cbfe-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2cbfe-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="2cbfe-114">**type**</span><span class="sxs-lookup"><span data-stu-id="2cbfe-114">**type**</span></span>|<span data-ttu-id="2cbfe-115">Nazwa modułu uwierzytelniania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cbfe-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2cbfe-116">Child Elements</span></span>  
 <span data-ttu-id="2cbfe-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cbfe-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2cbfe-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2cbfe-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="2cbfe-119">**Element**</span></span>|<span data-ttu-id="2cbfe-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2cbfe-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2cbfe-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="2cbfe-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="2cbfe-122">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cbfe-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cbfe-123">Remarks</span></span>  
 <span data-ttu-id="2cbfe-124">`remove` Element usuwa moduły uwierzytelniania zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="2cbfe-125">Wartość `type` atrybutu powinna być prawidłową nazwą klasy.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2cbfe-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2cbfe-126">Configuration Files</span></span>  
 <span data-ttu-id="2cbfe-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2cbfe-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cbfe-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="2cbfe-128">Example</span></span>  
 <span data-ttu-id="2cbfe-129">Poniższy przykład usuwa moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cbfe-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cbfe-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="2cbfe-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2cbfe-131">Network Settings Schema</span></span>](index.md)
