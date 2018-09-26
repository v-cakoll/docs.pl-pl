---
title: '&lt;Dodaj&gt; Element dla authenticationModules (ustawienia sieci)'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4a9bcc6cd5d2bbf30f463da0a51e1bccbcd5a3f1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083890"
---
# <a name="ltaddgt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="706ac-102">&lt;Dodaj&gt; Element dla authenticationModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="706ac-102">&lt;add&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="706ac-103">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="706ac-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="706ac-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="706ac-104">\<configuration></span></span>  
<span data-ttu-id="706ac-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="706ac-105">\<system.net></span></span>  
<span data-ttu-id="706ac-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="706ac-106">\<authenticationModules></span></span>  
<span data-ttu-id="706ac-107">\<add></span><span class="sxs-lookup"><span data-stu-id="706ac-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="706ac-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="706ac-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="706ac-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="706ac-109">Attributes and Elements</span></span>  
 <span data-ttu-id="706ac-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="706ac-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="706ac-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="706ac-111">Attributes</span></span>  
  
|<span data-ttu-id="706ac-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="706ac-112">**Attribute**</span></span>|<span data-ttu-id="706ac-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="706ac-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="706ac-114">W pełni kwalifikowana nazwa typu (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="706ac-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="706ac-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="706ac-115">Child Elements</span></span>  
 <span data-ttu-id="706ac-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="706ac-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="706ac-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="706ac-117">Parent Elements</span></span>  
  
|<span data-ttu-id="706ac-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="706ac-118">**Element**</span></span>|<span data-ttu-id="706ac-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="706ac-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="706ac-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="706ac-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="706ac-121">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="706ac-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="706ac-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="706ac-122">Remarks</span></span>  
 <span data-ttu-id="706ac-123">`add` Elementu dodaje moduł uwierzytelniania na końcu listy modułów uwierzytelniania zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="706ac-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="706ac-124">Moduły uwierzytelniania są wywoływane w kolejności, w jakiej zostały dodane do listy.</span><span class="sxs-lookup"><span data-stu-id="706ac-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="706ac-125">Wartość `type` atrybut powinien być prawidłową nazwą typu i odpowiedniej nazwy zestawu, oddzielając wartości przecinkami.</span><span class="sxs-lookup"><span data-stu-id="706ac-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="706ac-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="706ac-126">Configuration Files</span></span>  
 <span data-ttu-id="706ac-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="706ac-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="706ac-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="706ac-128">Example</span></span>  
 <span data-ttu-id="706ac-129">Poniższy przykład umożliwia domyślne moduły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="706ac-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="706ac-130">Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="706ac-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="706ac-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="706ac-131">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="706ac-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="706ac-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
