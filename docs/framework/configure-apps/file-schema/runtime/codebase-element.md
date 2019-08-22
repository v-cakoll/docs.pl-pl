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
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663865"
---
# <a name="codebase-element"></a><span data-ttu-id="b2f0f-102">\<codeBase> Element</span><span class="sxs-lookup"><span data-stu-id="b2f0f-102">\<codeBase> Element</span></span>

<span data-ttu-id="b2f0f-103">Określa, gdzie środowisko uruchomieniowe języka wspólnego może znaleźć zestaw.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="b2f0f-104">\<Configuration > \<Runtime > \<assemblyBinding > \<dependentAssembly > \<codebase ></span><span class="sxs-lookup"><span data-stu-id="b2f0f-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="b2f0f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2f0f-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2f0f-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b2f0f-106">Attributes and Elements</span></span>

<span data-ttu-id="b2f0f-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2f0f-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b2f0f-108">Attributes</span></span>

|<span data-ttu-id="b2f0f-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b2f0f-109">Attribute</span></span>|<span data-ttu-id="b2f0f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b2f0f-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="b2f0f-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="b2f0f-112">Określa adres URL, pod którym środowisko uruchomieniowe może znaleźć określoną wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="b2f0f-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b2f0f-114">Określa wersję zestawu, którego dotyczy baza kodu.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="b2f0f-115">Format numeru wersji zestawu to *główna. pomocnicza. kompilacja. poprawka*.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="b2f0f-116">Atrybut wersji</span><span class="sxs-lookup"><span data-stu-id="b2f0f-116">version Attribute</span></span>

|<span data-ttu-id="b2f0f-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="b2f0f-117">Value</span></span>|<span data-ttu-id="b2f0f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b2f0f-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="b2f0f-119">Prawidłowe wartości dla każdej części numeru wersji to 0 – 65535.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="b2f0f-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b2f0f-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b2f0f-121">Child Elements</span></span>

<span data-ttu-id="b2f0f-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2f0f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b2f0f-123">Parent Elements</span></span>

|<span data-ttu-id="b2f0f-124">Element</span><span class="sxs-lookup"><span data-stu-id="b2f0f-124">Element</span></span>|<span data-ttu-id="b2f0f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b2f0f-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="b2f0f-126">Definiuje kolekcję dostawców kompilacji używanych do kompilowania niestandardowych plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="b2f0f-127">Możesz mieć dowolną liczbę dostawców kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="b2f0f-128">Konfiguruje wszystkie ustawienia kompilacji, które są używane przez ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="b2f0f-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="b2f0f-130">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2f0f-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2f0f-131">Remarks</span></span>

<span data-ttu-id="b2f0f-132">Aby środowisko uruchomieniowe korzystało z  **\<bazy kodu >** w pliku konfiguracyjnym komputera lub w pliku zasad wydawcy, plik musi również przekierować wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="b2f0f-133">Pliki konfiguracji aplikacji mogą mieć ustawienie bazy kodu bez przekierowywania wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="b2f0f-134">Po ustaleniu, która wersja zestawu ma być używana, środowisko uruchomieniowe stosuje ustawienie bazy kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="b2f0f-135">Jeśli nie jest wskazana baza kodu, sondy środowiska uruchomieniowego dla zestawu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="b2f0f-136">Jeśli zestaw ma silną nazwę, ustawienie codebase może znajdować się w dowolnym miejscu w lokalnym intranecie lub w Internecie.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="b2f0f-137">Jeśli zestaw jest zestawem prywatnym, ustawienie bazy kodu musi być ścieżką względną do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="b2f0f-138">W przypadku zestawów bez silnej nazwy wersja jest ignorowana, a moduł ładujący używa pierwszego \<wyglądu kodu bazowej \<> wewnątrz dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="b2f0f-139">Jeśli w pliku konfiguracyjnym aplikacji znajduje się wpis służący do przekierowywania powiązań do innego zestawu, przekierowania będzie miało pierwszeństwo, nawet jeśli wersja zestawu nie jest zgodna z żądaniem powiązania.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="b2f0f-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2f0f-140">Example</span></span>

<span data-ttu-id="b2f0f-141">Poniższy przykład pokazuje, jak określić, gdzie środowisko uruchomieniowe może znaleźć zestaw.</span><span class="sxs-lookup"><span data-stu-id="b2f0f-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b2f0f-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2f0f-142">See also</span></span>

- [<span data-ttu-id="b2f0f-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b2f0f-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b2f0f-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b2f0f-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b2f0f-145">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="b2f0f-145">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="b2f0f-146">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b2f0f-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
