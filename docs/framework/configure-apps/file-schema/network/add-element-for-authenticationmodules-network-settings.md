---
title: <add>, element dla authenticationModules (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: a68434aaa118db60a502c2bcc0bb188b83b0f463
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698428"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="86b52-102">\<add > elementu authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="86b52-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="86b52-103">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86b52-103">Adds an authentication module to the application.</span></span>  
  
[<span data-ttu-id="86b52-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="86b52-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="86b52-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="86b52-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="86b52-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="86b52-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="86b52-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="86b52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b52-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="86b52-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86b52-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="86b52-109">Attributes and Elements</span></span>  
 <span data-ttu-id="86b52-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="86b52-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86b52-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="86b52-111">Attributes</span></span>  
  
|<span data-ttu-id="86b52-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="86b52-112">**Attribute**</span></span>|<span data-ttu-id="86b52-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="86b52-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="86b52-114">W pełni kwalifikowana nazwa typu (wskazywana przez właściwość <xref:System.Type.FullName%2A>) i nazwa zestawu (wskazywanym przez właściwość <xref:System.Reflection.Assembly.FullName%2A>) oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="86b52-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86b52-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="86b52-115">Child Elements</span></span>  
 <span data-ttu-id="86b52-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="86b52-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86b52-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="86b52-117">Parent Elements</span></span>  
  
|<span data-ttu-id="86b52-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="86b52-118">**Element**</span></span>|<span data-ttu-id="86b52-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="86b52-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="86b52-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="86b52-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="86b52-121">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="86b52-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86b52-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86b52-122">Remarks</span></span>  
 <span data-ttu-id="86b52-123">Element `add` dodaje moduł uwierzytelniania na końcu listy zarejestrowanych modułów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="86b52-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="86b52-124">Moduły uwierzytelniania są wywoływane w kolejności, w jakiej zostały dodane do listy.</span><span class="sxs-lookup"><span data-stu-id="86b52-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="86b52-125">Wartość atrybutu `type` powinna być prawidłową nazwą typu i odpowiadającą jej nazwą zestawu, rozdzieloną przecinkami.</span><span class="sxs-lookup"><span data-stu-id="86b52-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="86b52-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="86b52-126">Configuration Files</span></span>  
 <span data-ttu-id="86b52-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="86b52-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86b52-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="86b52-128">Example</span></span>  
 <span data-ttu-id="86b52-129">W poniższym przykładzie są włączane domyślne moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="86b52-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="86b52-130">Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="86b52-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86b52-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86b52-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="86b52-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="86b52-132">Network Settings Schema</span></span>](index.md)
