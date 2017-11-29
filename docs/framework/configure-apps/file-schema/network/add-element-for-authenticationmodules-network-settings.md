---
title: "&lt;Dodaj&gt; elementu authenticationModules — (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 60909a738afbe2ec14d0f67846b06578a7393601
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="1f4d9-102">&lt;Dodaj&gt; elementu authenticationModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="1f4d9-102">&lt;add&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="1f4d9-103">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="1f4d9-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1f4d9-104">\<configuration></span></span>  
<span data-ttu-id="1f4d9-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="1f4d9-105">\<system.net></span></span>  
<span data-ttu-id="1f4d9-106">\<authenticationModules — ></span><span class="sxs-lookup"><span data-stu-id="1f4d9-106">\<authenticationModules></span></span>  
<span data-ttu-id="1f4d9-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="1f4d9-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4d9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f4d9-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f4d9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f4d9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1f4d9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f4d9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f4d9-111">Attributes</span></span>  
  
|<span data-ttu-id="1f4d9-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="1f4d9-112">**Attribute**</span></span>|<span data-ttu-id="1f4d9-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1f4d9-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="1f4d9-114">Nazwa typu w pełni kwalifikowana (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f4d9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f4d9-115">Child Elements</span></span>  
 <span data-ttu-id="1f4d9-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f4d9-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f4d9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1f4d9-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="1f4d9-118">**Element**</span></span>|<span data-ttu-id="1f4d9-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1f4d9-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1f4d9-120">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="1f4d9-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="1f4d9-121">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f4d9-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f4d9-122">Remarks</span></span>  
 <span data-ttu-id="1f4d9-123">`add` Element dodaje moduł uwierzytelniania na końcu listy modułów zarejestrowanych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="1f4d9-124">Moduły uwierzytelniania są wywoływane w kolejności, w jakiej zostały dodane do listy.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="1f4d9-125">Wartość `type` atrybutu powinna być prawidłową nazwą typu i odpowiadającą jej nazwą zestawu, rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1f4d9-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1f4d9-126">Configuration Files</span></span>  
 <span data-ttu-id="1f4d9-127">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="1f4d9-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f4d9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f4d9-128">Example</span></span>  
 <span data-ttu-id="1f4d9-129">Poniższy przykład umożliwia domyślne moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="1f4d9-130">Wartości należy zastąpić wersję i PublicKeyToken przy użyciu prawidłowych wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="1f4d9-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f4d9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f4d9-131">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="1f4d9-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="1f4d9-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
