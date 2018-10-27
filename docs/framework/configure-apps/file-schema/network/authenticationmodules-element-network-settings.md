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
ms.openlocfilehash: 074f2f0cd2c3ac6c6287db08b22ead07afa58fc5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190817"
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="f3ca8-102">&lt;authenticationModules&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f3ca8-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f3ca8-103">Określa moduły używane do uwierzytelniania żądań w sieci.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="f3ca8-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f3ca8-104">\<configuration></span></span>  
<span data-ttu-id="f3ca8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f3ca8-105">\<system.net></span></span>  
<span data-ttu-id="f3ca8-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="f3ca8-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ca8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3ca8-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3ca8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3ca8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3ca8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3ca8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3ca8-110">Attributes</span></span>  
 <span data-ttu-id="f3ca8-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3ca8-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3ca8-112">Child Elements</span></span>  
  
|<span data-ttu-id="f3ca8-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="f3ca8-113">**Element**</span></span>|<span data-ttu-id="f3ca8-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f3ca8-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3ca8-115">add</span><span class="sxs-lookup"><span data-stu-id="f3ca8-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="f3ca8-116">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="f3ca8-117">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="f3ca8-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="f3ca8-118">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="f3ca8-119">remove</span><span class="sxs-lookup"><span data-stu-id="f3ca8-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="f3ca8-120">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3ca8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3ca8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3ca8-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="f3ca8-122">**Element**</span></span>|<span data-ttu-id="f3ca8-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f3ca8-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3ca8-124">przestrzeni nazw System.NET</span><span class="sxs-lookup"><span data-stu-id="f3ca8-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="f3ca8-125">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3ca8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3ca8-126">Remarks</span></span>  
 <span data-ttu-id="f3ca8-127">`authenticationModule` Element określa moduły uwierzytelniania, które należy przeprowadzić proces uwierzytelniania z serwerem.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="f3ca8-128">Moduł uwierzytelniania musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f3ca8-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f3ca8-129">Configuration Files</span></span>  
 <span data-ttu-id="f3ca8-130">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f3ca8-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ca8-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3ca8-131">Example</span></span>  
 <span data-ttu-id="f3ca8-132">Poniższy przykład umożliwia moduł uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-132">The following example enables an authentication module.</span></span> <span data-ttu-id="f3ca8-133">Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="f3ca8-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3ca8-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3ca8-134">See Also</span></span>  
- <xref:System.Net.IAuthenticationModule>  
- <xref:System.Net.AuthenticationManager>  
- [<span data-ttu-id="f3ca8-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f3ca8-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
