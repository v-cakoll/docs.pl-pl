---
title: '&lt;authenticationModules&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: d143f91d31951f218631519a3182f5de6c4eca60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532126"
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="e3341-102">&lt;authenticationModules&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e3341-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e3341-103">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="e3341-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="e3341-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="e3341-104">\<configuration></span></span>  
<span data-ttu-id="e3341-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e3341-105">\<system.net></span></span>  
<span data-ttu-id="e3341-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="e3341-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3341-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3341-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3341-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3341-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e3341-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3341-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3341-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3341-110">Attributes</span></span>  
 <span data-ttu-id="e3341-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e3341-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3341-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3341-112">Child Elements</span></span>  
  
|<span data-ttu-id="e3341-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="e3341-113">**Element**</span></span>|<span data-ttu-id="e3341-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e3341-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e3341-115">add</span><span class="sxs-lookup"><span data-stu-id="e3341-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="e3341-116">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3341-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="e3341-117">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="e3341-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="e3341-118">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3341-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="e3341-119">remove</span><span class="sxs-lookup"><span data-stu-id="e3341-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="e3341-120">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3341-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3341-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3341-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e3341-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="e3341-122">**Element**</span></span>|<span data-ttu-id="e3341-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e3341-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e3341-124">system.net</span><span class="sxs-lookup"><span data-stu-id="e3341-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="e3341-125">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="e3341-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3341-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3341-126">Remarks</span></span>  
 <span data-ttu-id="e3341-127">`authenticationModule` Element określa moduły uwierzytelniania, które należy przeprowadzić proces uwierzytelniania z serwerem.</span><span class="sxs-lookup"><span data-stu-id="e3341-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="e3341-128">Moduł uwierzytelniania musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e3341-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e3341-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e3341-129">Configuration Files</span></span>  
 <span data-ttu-id="e3341-130">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e3341-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3341-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3341-131">Example</span></span>  
 <span data-ttu-id="e3341-132">Poniższy przykład umożliwia moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e3341-132">The following example enables an authentication module.</span></span> <span data-ttu-id="e3341-133">Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="e3341-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3341-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3341-134">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="e3341-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e3341-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
