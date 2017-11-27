---
title: "&lt;w parametrze bindingRedirect&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bc8abc019ddb271c8c1246b280be754585bfd61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingredirectgt-element"></a><span data-ttu-id="55a67-102">&lt;w parametrze bindingRedirect&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="55a67-102">&lt;bindingRedirect&gt; Element</span></span>
<span data-ttu-id="55a67-103">Przekierowuje jedną wersję zestawu do innej.</span><span class="sxs-lookup"><span data-stu-id="55a67-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="55a67-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="55a67-104">\<configuration></span></span>  
<span data-ttu-id="55a67-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="55a67-105">\<runtime></span></span>  
<span data-ttu-id="55a67-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="55a67-106">\<assemblyBinding></span></span>  
<span data-ttu-id="55a67-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="55a67-107">\<dependentAssembly></span></span>  
<span data-ttu-id="55a67-108">\<w parametrze bindingRedirect ></span><span class="sxs-lookup"><span data-stu-id="55a67-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a67-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="55a67-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55a67-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55a67-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55a67-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55a67-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55a67-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55a67-112">Attributes</span></span>  
  
|<span data-ttu-id="55a67-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="55a67-113">Attribute</span></span>|<span data-ttu-id="55a67-114">Opis</span><span class="sxs-lookup"><span data-stu-id="55a67-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="55a67-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="55a67-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="55a67-116">Określa pierwotnie żądaną wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="55a67-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="55a67-117">Format numeru wersji zestawu jest *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="55a67-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="55a67-118">Prawidłowe wartości każdej części tego numeru wersji należą do zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="55a67-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="55a67-119">Można również określić zakres wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="55a67-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="55a67-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="55a67-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="55a67-121">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="55a67-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="55a67-122">Określa wersję zestawu do użycia zamiast pierwotnie żądanej wersji w formacie: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="55a67-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="55a67-123">Tę wartość można określić wersji starszej niż `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="55a67-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55a67-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55a67-124">Child Elements</span></span>  
  
|<span data-ttu-id="55a67-125">Element</span><span class="sxs-lookup"><span data-stu-id="55a67-125">Element</span></span>|<span data-ttu-id="55a67-126">Opis</span><span class="sxs-lookup"><span data-stu-id="55a67-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55a67-127">Brak</span><span class="sxs-lookup"><span data-stu-id="55a67-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="55a67-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55a67-128">Parent Elements</span></span>  
  
|<span data-ttu-id="55a67-129">Element</span><span class="sxs-lookup"><span data-stu-id="55a67-129">Element</span></span>|<span data-ttu-id="55a67-130">Opis</span><span class="sxs-lookup"><span data-stu-id="55a67-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="55a67-131">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="55a67-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="55a67-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55a67-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="55a67-133">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="55a67-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="55a67-134">Dla każdego zestawu należy użyć jednego elementu dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="55a67-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="55a67-135">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="55a67-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55a67-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55a67-136">Remarks</span></span>  
 <span data-ttu-id="55a67-137">W przypadku skompilowania aplikacji programu .NET Framework z użyciem zestawu o silnej nazwie aplikacja domyślnie używa tej wersji w czasie działania, nawet jeśli jest dostępna nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="55a67-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="55a67-138">Można jednak skonfigurować aplikację do działania z użyciem nowszej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="55a67-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="55a67-139">Szczegółowe informacje dotyczące sposobu środowiska uruchomieniowego używa tych plików w celu określenia wersji zestawu do użycia, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="55a67-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="55a67-140">Można przekierować więcej niż jedną wersję zestawu przez dołączenie wielu `bindingRedirect` elementów w `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="55a67-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="55a67-141">Można również wykonać przekierowanie z nowszej wersji zestawu do starszej.</span><span class="sxs-lookup"><span data-stu-id="55a67-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="55a67-142">Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="55a67-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="55a67-143">Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich.</span><span class="sxs-lookup"><span data-stu-id="55a67-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="55a67-144">Uprawnienie zostanie udzielone przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> Flaga na <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="55a67-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="55a67-145">Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="55a67-145">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55a67-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="55a67-146">Example</span></span>  
 <span data-ttu-id="55a67-147">W poniższym przykładzie pokazano sposób przekierowywania wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="55a67-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55a67-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55a67-148">See Also</span></span>  
 [<span data-ttu-id="55a67-149">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="55a67-149">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="55a67-150">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55a67-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="55a67-151">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="55a67-151">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
