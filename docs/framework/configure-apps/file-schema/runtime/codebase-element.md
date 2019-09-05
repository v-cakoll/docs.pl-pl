---
title: <codeBase>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: bd170b817c5ccc337711f8f79968653c29f3eda4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252743"
---
# <a name="codebase-element"></a><span data-ttu-id="ca74b-102">\<codeBase> Element</span><span class="sxs-lookup"><span data-stu-id="ca74b-102">\<codeBase> Element</span></span>

<span data-ttu-id="ca74b-103">Określa, gdzie środowisko uruchomieniowe języka wspólnego może znaleźć zestaw.</span><span class="sxs-lookup"><span data-stu-id="ca74b-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="ca74b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca74b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca74b-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca74b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ca74b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="ca74b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="ca74b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca74b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="ca74b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**</span><span class="sxs-lookup"><span data-stu-id="ca74b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ca74b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca74b-109">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca74b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca74b-110">Attributes and Elements</span></span>

<span data-ttu-id="ca74b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca74b-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca74b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca74b-112">Attributes</span></span>

|<span data-ttu-id="ca74b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca74b-113">Attribute</span></span>|<span data-ttu-id="ca74b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ca74b-114">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="ca74b-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ca74b-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca74b-116">Określa adres URL, pod którym środowisko uruchomieniowe może znaleźć określoną wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="ca74b-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="ca74b-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ca74b-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca74b-118">Określa wersję zestawu, którego dotyczy baza kodu.</span><span class="sxs-lookup"><span data-stu-id="ca74b-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="ca74b-119">Format numeru wersji zestawu to *główna. pomocnicza. kompilacja. poprawka*.</span><span class="sxs-lookup"><span data-stu-id="ca74b-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="ca74b-120">Atrybut wersji</span><span class="sxs-lookup"><span data-stu-id="ca74b-120">version Attribute</span></span>

|<span data-ttu-id="ca74b-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="ca74b-121">Value</span></span>|<span data-ttu-id="ca74b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ca74b-122">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="ca74b-123">Prawidłowe wartości dla każdej części numeru wersji to 0 – 65535.</span><span class="sxs-lookup"><span data-stu-id="ca74b-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="ca74b-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ca74b-124">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ca74b-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca74b-125">Child Elements</span></span>

<span data-ttu-id="ca74b-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="ca74b-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca74b-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca74b-127">Parent Elements</span></span>

|<span data-ttu-id="ca74b-128">Element</span><span class="sxs-lookup"><span data-stu-id="ca74b-128">Element</span></span>|<span data-ttu-id="ca74b-129">Opis</span><span class="sxs-lookup"><span data-stu-id="ca74b-129">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="ca74b-130">Definiuje kolekcję dostawców kompilacji używanych do kompilowania niestandardowych plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="ca74b-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="ca74b-131">Możesz mieć dowolną liczbę dostawców kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ca74b-131">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="ca74b-132">Konfiguruje wszystkie ustawienia kompilacji, które są używane przez ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ca74b-132">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="ca74b-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca74b-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="ca74b-134">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ca74b-134">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca74b-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca74b-135">Remarks</span></span>

<span data-ttu-id="ca74b-136">Aby środowisko uruchomieniowe korzystało z  **\<bazy kodu >** w pliku konfiguracyjnym komputera lub w pliku zasad wydawcy, plik musi również przekierować wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="ca74b-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="ca74b-137">Pliki konfiguracji aplikacji mogą mieć ustawienie bazy kodu bez przekierowywania wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="ca74b-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="ca74b-138">Po ustaleniu, która wersja zestawu ma być używana, środowisko uruchomieniowe stosuje ustawienie bazy kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="ca74b-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="ca74b-139">Jeśli nie jest wskazana baza kodu, sondy środowiska uruchomieniowego dla zestawu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="ca74b-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="ca74b-140">Jeśli zestaw ma silną nazwę, ustawienie codebase może znajdować się w dowolnym miejscu w lokalnym intranecie lub w Internecie.</span><span class="sxs-lookup"><span data-stu-id="ca74b-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="ca74b-141">Jeśli zestaw jest zestawem prywatnym, ustawienie bazy kodu musi być ścieżką względną do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca74b-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="ca74b-142">W przypadku zestawów bez silnej nazwy wersja jest ignorowana, a moduł ładujący używa pierwszego \<wyglądu kodu bazowej \<> wewnątrz dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="ca74b-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="ca74b-143">Jeśli w pliku konfiguracyjnym aplikacji znajduje się wpis służący do przekierowywania powiązań do innego zestawu, przekierowania będzie miało pierwszeństwo, nawet jeśli wersja zestawu nie jest zgodna z żądaniem powiązania.</span><span class="sxs-lookup"><span data-stu-id="ca74b-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="ca74b-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca74b-144">Example</span></span>

<span data-ttu-id="ca74b-145">Poniższy przykład pokazuje, jak określić, gdzie środowisko uruchomieniowe może znaleźć zestaw.</span><span class="sxs-lookup"><span data-stu-id="ca74b-145">The following example shows how to specify where the runtime can find an assembly.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ca74b-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca74b-146">See also</span></span>

- [<span data-ttu-id="ca74b-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ca74b-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca74b-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ca74b-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ca74b-149">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="ca74b-149">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="ca74b-150">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ca74b-150">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
