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
ms.openlocfilehash: d72371921a85ff5a68dd9017f0fe8cf5d28557dd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664238"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="b969e-102">\<Dodaj element > dla authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="b969e-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="b969e-103">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b969e-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="b969e-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b969e-104">\<configuration></span></span>  
<span data-ttu-id="b969e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b969e-105">\<system.net></span></span>  
<span data-ttu-id="b969e-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="b969e-106">\<authenticationModules></span></span>  
<span data-ttu-id="b969e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b969e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b969e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b969e-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b969e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b969e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b969e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b969e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b969e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b969e-111">Attributes</span></span>  
  
|<span data-ttu-id="b969e-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="b969e-112">**Attribute**</span></span>|<span data-ttu-id="b969e-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b969e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="b969e-114">W pełni kwalifikowana nazwa typu (wskazywana przez <xref:System.Type.FullName%2A> Właściwość) i nazwa zestawu (wskazywanym <xref:System.Reflection.Assembly.FullName%2A> przez właściwość) oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b969e-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b969e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b969e-115">Child Elements</span></span>  
 <span data-ttu-id="b969e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="b969e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b969e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b969e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b969e-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="b969e-118">**Element**</span></span>|<span data-ttu-id="b969e-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b969e-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b969e-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="b969e-120">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="b969e-121">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="b969e-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b969e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b969e-122">Remarks</span></span>  
 <span data-ttu-id="b969e-123">`add` Element dodaje moduł uwierzytelniania na końcu listy zarejestrowanych modułów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="b969e-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="b969e-124">Moduły uwierzytelniania są wywoływane w kolejności, w jakiej zostały dodane do listy.</span><span class="sxs-lookup"><span data-stu-id="b969e-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="b969e-125">Wartość `type` atrybutu powinna być prawidłową nazwą typu i odpowiadającą jej nazwą zestawu, rozdzieloną przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b969e-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b969e-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b969e-126">Configuration Files</span></span>  
 <span data-ttu-id="b969e-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b969e-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b969e-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="b969e-128">Example</span></span>  
 <span data-ttu-id="b969e-129">W poniższym przykładzie są włączane domyślne moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="b969e-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="b969e-130">Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="b969e-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b969e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b969e-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="b969e-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b969e-132">Network Settings Schema</span></span>](index.md)
