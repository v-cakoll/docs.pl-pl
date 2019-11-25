---
title: <authenticationModules>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: bacaaf92464a355804a9ea8307f6e6f1caac1f05
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087610"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="1db73-102">\<element > authenticationModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="1db73-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="1db73-103">Określa moduły używane do uwierzytelniania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="1db73-103">Specifies modules used to authenticate network requests.</span></span>  

<span data-ttu-id="1db73-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1db73-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1db73-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1db73-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="1db73-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="1db73-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1db73-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1db73-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1db73-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1db73-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1db73-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1db73-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1db73-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1db73-110">Attributes</span></span>  
 <span data-ttu-id="1db73-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="1db73-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1db73-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1db73-112">Child Elements</span></span>  
  
|<span data-ttu-id="1db73-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="1db73-113">**Element**</span></span>|<span data-ttu-id="1db73-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1db73-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1db73-115">add</span><span class="sxs-lookup"><span data-stu-id="1db73-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="1db73-116">Dodaje moduł uwierzytelniania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1db73-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="1db73-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="1db73-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="1db73-118">Czyści wszystkie moduły uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1db73-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="1db73-119">remove</span><span class="sxs-lookup"><span data-stu-id="1db73-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="1db73-120">Usuwa moduł uwierzytelniania z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1db73-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1db73-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1db73-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1db73-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="1db73-122">**Element**</span></span>|<span data-ttu-id="1db73-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1db73-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1db73-124">system.net</span><span class="sxs-lookup"><span data-stu-id="1db73-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="1db73-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="1db73-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db73-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1db73-126">Remarks</span></span>  
 <span data-ttu-id="1db73-127">`authenticationModule` element określa moduły uwierzytelniania, które przeprowadzą proces uwierzytelniania z serwerem.</span><span class="sxs-lookup"><span data-stu-id="1db73-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="1db73-128">Moduł uwierzytelniania musi implementować interfejs <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="1db73-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1db73-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1db73-129">Configuration Files</span></span>  
 <span data-ttu-id="1db73-130">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1db73-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db73-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="1db73-131">Example</span></span>  
 <span data-ttu-id="1db73-132">Poniższy przykład umożliwia włączenie modułu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1db73-132">The following example enables an authentication module.</span></span> <span data-ttu-id="1db73-133">Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="1db73-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1db73-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1db73-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="1db73-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="1db73-135">Network Settings Schema</span></span>](index.md)
