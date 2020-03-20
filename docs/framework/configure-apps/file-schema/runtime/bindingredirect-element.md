---
title: <bindingRedirect>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154299"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="7d028-102">\<element> bindingRedirect</span><span class="sxs-lookup"><span data-stu-id="7d028-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="7d028-103">Przekierowuje jedną wersję zestawu do innej.</span><span class="sxs-lookup"><span data-stu-id="7d028-103">Redirects one assembly version to another.</span></span>  
  
<span data-ttu-id="7d028-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d028-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d028-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d028-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7d028-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>montażowy**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="7d028-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="7d028-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d028-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="7d028-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>bindingRedirect**</span><span class="sxs-lookup"><span data-stu-id="7d028-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d028-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d028-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d028-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d028-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d028-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d028-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d028-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d028-112">Attributes</span></span>  
  
|<span data-ttu-id="7d028-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d028-113">Attribute</span></span>|<span data-ttu-id="7d028-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7d028-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="7d028-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7d028-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="7d028-116">Określa pierwotnie żądaną wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d028-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="7d028-117">Format numeru wersji zestawu to *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="7d028-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="7d028-118">Prawidłowe wartości każdej części tego numeru wersji należą do zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="7d028-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="7d028-119">Można również określić zakres wersji w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="7d028-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="7d028-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="7d028-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="7d028-121">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7d028-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="7d028-122">Określa wersję zestawu, która ma być używana zamiast pierwotnie żądanej wersji w formacie: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="7d028-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="7d028-123">Ta wartość może określić `oldVersion`wcześniejszą wersję niż .</span><span class="sxs-lookup"><span data-stu-id="7d028-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d028-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d028-124">Child Elements</span></span>  
  
|<span data-ttu-id="7d028-125">Element</span><span class="sxs-lookup"><span data-stu-id="7d028-125">Element</span></span>|<span data-ttu-id="7d028-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7d028-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d028-127">Brak</span><span class="sxs-lookup"><span data-stu-id="7d028-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="7d028-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d028-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7d028-129">Element</span><span class="sxs-lookup"><span data-stu-id="7d028-129">Element</span></span>|<span data-ttu-id="7d028-130">Opis</span><span class="sxs-lookup"><span data-stu-id="7d028-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="7d028-131">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="7d028-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="7d028-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d028-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="7d028-133">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d028-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="7d028-134">Dla każdego zestawu należy użyć jednego elementu dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="7d028-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="7d028-135">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7d028-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d028-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d028-136">Remarks</span></span>  
 <span data-ttu-id="7d028-137">W przypadku skompilowania aplikacji programu .NET Framework z użyciem zestawu o silnej nazwie aplikacja domyślnie używa tej wersji w czasie działania, nawet jeśli jest dostępna nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="7d028-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="7d028-138">Można jednak skonfigurować aplikację do działania z użyciem nowszej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d028-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="7d028-139">Aby uzyskać szczegółowe informacje na temat sposobu, w jaki środowisko wykonawcze używa tych plików do określenia, której wersji zestawu użyć, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7d028-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="7d028-140">Można przekierować więcej niż jedną `bindingRedirect` wersję zestawu, dołączając wiele elementów w elemencie. `dependentAssembly`</span><span class="sxs-lookup"><span data-stu-id="7d028-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="7d028-141">Można również wykonać przekierowanie z nowszej wersji zestawu do starszej.</span><span class="sxs-lookup"><span data-stu-id="7d028-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="7d028-142">Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7d028-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="7d028-143">Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich.</span><span class="sxs-lookup"><span data-stu-id="7d028-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="7d028-144">Uprawnienie jest przyznawane <xref:System.Security.Permissions.SecurityPermissionFlag> przez ustawienie <xref:System.Security.Permissions.SecurityPermission>flagi na pliku .</span><span class="sxs-lookup"><span data-stu-id="7d028-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="7d028-145">Aby uzyskać więcej informacji, zobacz [Uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="7d028-145">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d028-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d028-146">Example</span></span>  
 <span data-ttu-id="7d028-147">W poniższym przykładzie pokazano sposób przekierowywania wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d028-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d028-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d028-148">See also</span></span>

- [<span data-ttu-id="7d028-149">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7d028-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7d028-150">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7d028-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7d028-151">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="7d028-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
