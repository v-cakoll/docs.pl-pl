---
title: '&lt;bindingRedirect&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 535519c65aba7ce13703bb33a16b09cde84c3f03
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085557"
---
# <a name="ltbindingredirectgt-element"></a><span data-ttu-id="71a44-102">&lt;bindingRedirect&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="71a44-102">&lt;bindingRedirect&gt; Element</span></span>
<span data-ttu-id="71a44-103">Przekierowuje jedną wersję zestawu do innej.</span><span class="sxs-lookup"><span data-stu-id="71a44-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="71a44-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="71a44-104">\<configuration></span></span>  
<span data-ttu-id="71a44-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="71a44-105">\<runtime></span></span>  
<span data-ttu-id="71a44-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="71a44-106">\<assemblyBinding></span></span>  
<span data-ttu-id="71a44-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="71a44-107">\<dependentAssembly></span></span>  
<span data-ttu-id="71a44-108">\<bindingRedirect ></span><span class="sxs-lookup"><span data-stu-id="71a44-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a44-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="71a44-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71a44-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="71a44-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71a44-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="71a44-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71a44-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71a44-112">Attributes</span></span>  
  
|<span data-ttu-id="71a44-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="71a44-113">Attribute</span></span>|<span data-ttu-id="71a44-114">Opis</span><span class="sxs-lookup"><span data-stu-id="71a44-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="71a44-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="71a44-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="71a44-116">Określa pierwotnie żądaną wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="71a44-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="71a44-117">Format numeru wersji zestawu to *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="71a44-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="71a44-118">Prawidłowe wartości każdej części tego numeru wersji należą do zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="71a44-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="71a44-119">Można również określić zakres wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="71a44-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="71a44-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="71a44-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="71a44-121">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="71a44-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="71a44-122">Określa numer wersji zestawu do użycia zamiast pierwotnie żądanej wersji w formacie: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="71a44-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="71a44-123">Ta wartość może określać w wersji starszej niż `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="71a44-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71a44-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71a44-124">Child Elements</span></span>  
  
|<span data-ttu-id="71a44-125">Element</span><span class="sxs-lookup"><span data-stu-id="71a44-125">Element</span></span>|<span data-ttu-id="71a44-126">Opis</span><span class="sxs-lookup"><span data-stu-id="71a44-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71a44-127">Brak</span><span class="sxs-lookup"><span data-stu-id="71a44-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="71a44-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71a44-128">Parent Elements</span></span>  
  
|<span data-ttu-id="71a44-129">Element</span><span class="sxs-lookup"><span data-stu-id="71a44-129">Element</span></span>|<span data-ttu-id="71a44-130">Opis</span><span class="sxs-lookup"><span data-stu-id="71a44-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="71a44-131">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="71a44-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="71a44-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71a44-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="71a44-133">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="71a44-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="71a44-134">Dla każdego zestawu należy użyć jednego elementu dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="71a44-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="71a44-135">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="71a44-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71a44-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71a44-136">Remarks</span></span>  
 <span data-ttu-id="71a44-137">W przypadku skompilowania aplikacji programu .NET Framework z użyciem zestawu o silnej nazwie aplikacja domyślnie używa tej wersji w czasie działania, nawet jeśli jest dostępna nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="71a44-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="71a44-138">Można jednak skonfigurować aplikację do działania z użyciem nowszej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="71a44-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="71a44-139">Aby uzyskać szczegółowe informacje dotyczące jak środowisko wykonawcze używa tych plików Aby określić, jakiego zestawu należy użyć, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="71a44-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="71a44-140">Możesz przekierować więcej niż jednej wersji zestawu, umieszczając wiele `bindingRedirect` elementów w `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="71a44-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="71a44-141">Można również wykonać przekierowanie z nowszej wersji zestawu do starszej.</span><span class="sxs-lookup"><span data-stu-id="71a44-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="71a44-142">Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="71a44-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="71a44-143">Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich.</span><span class="sxs-lookup"><span data-stu-id="71a44-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="71a44-144">To uprawnienie jest przydzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagą <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="71a44-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="71a44-145">Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="71a44-145">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71a44-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="71a44-146">Example</span></span>  
 <span data-ttu-id="71a44-147">W poniższym przykładzie pokazano sposób przekierowywania wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="71a44-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71a44-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71a44-148">See Also</span></span>  
 [<span data-ttu-id="71a44-149">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="71a44-149">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="71a44-150">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="71a44-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="71a44-151">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="71a44-151">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
