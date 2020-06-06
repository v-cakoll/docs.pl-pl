---
title: <codeBase> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: 475b7df55ed509157c1da0aeb8f979de238c72b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70971890"
---
# <a name="codebase-element"></a><span data-ttu-id="b621b-102">\<codeBase> Element</span><span class="sxs-lookup"><span data-stu-id="b621b-102">\<codeBase> Element</span></span>

<span data-ttu-id="b621b-103">Określa, gdzie środowisko uruchomieniowe języka wspólnego może znaleźć zestaw.</span><span class="sxs-lookup"><span data-stu-id="b621b-103">Specifies where the common language runtime can find an assembly.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**

## <a name="syntax"></a><span data-ttu-id="b621b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b621b-104">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b621b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b621b-105">Attributes and Elements</span></span>

<span data-ttu-id="b621b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b621b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b621b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b621b-107">Attributes</span></span>

|<span data-ttu-id="b621b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b621b-108">Attribute</span></span>|<span data-ttu-id="b621b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b621b-109">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="b621b-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b621b-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b621b-111">Określa adres URL, pod którym środowisko uruchomieniowe może znaleźć określoną wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="b621b-111">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="b621b-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b621b-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="b621b-113">Określa wersję zestawu, którego dotyczy baza kodu.</span><span class="sxs-lookup"><span data-stu-id="b621b-113">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="b621b-114">Format numeru wersji zestawu to *główna. pomocnicza. kompilacja. poprawka*.</span><span class="sxs-lookup"><span data-stu-id="b621b-114">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="b621b-115">Atrybut wersji</span><span class="sxs-lookup"><span data-stu-id="b621b-115">version Attribute</span></span>

|<span data-ttu-id="b621b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b621b-116">Value</span></span>|<span data-ttu-id="b621b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b621b-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="b621b-118">Prawidłowe wartości dla każdej części numeru wersji to 0 – 65535.</span><span class="sxs-lookup"><span data-stu-id="b621b-118">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="b621b-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="b621b-119">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b621b-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b621b-120">Child Elements</span></span>

<span data-ttu-id="b621b-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="b621b-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b621b-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b621b-122">Parent Elements</span></span>

|<span data-ttu-id="b621b-123">Element</span><span class="sxs-lookup"><span data-stu-id="b621b-123">Element</span></span>|<span data-ttu-id="b621b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b621b-124">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="b621b-125">Definiuje kolekcję dostawców kompilacji używanych do kompilowania niestandardowych plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="b621b-125">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="b621b-126">Możesz mieć dowolną liczbę dostawców kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b621b-126">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="b621b-127">Konfiguruje wszystkie ustawienia kompilacji, które są używane przez ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b621b-127">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="b621b-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b621b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="b621b-129">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b621b-129">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b621b-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b621b-130">Remarks</span></span>

<span data-ttu-id="b621b-131">Aby środowisko uruchomieniowe używało **\<codeBase>** Ustawienia w pliku konfiguracji komputera lub pliku zasad wydawcy, plik musi również przekierować wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="b621b-131">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="b621b-132">Pliki konfiguracji aplikacji mogą mieć ustawienie bazy kodu bez przekierowywania wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="b621b-132">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="b621b-133">Po ustaleniu, która wersja zestawu ma być używana, środowisko uruchomieniowe stosuje ustawienie bazy kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="b621b-133">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="b621b-134">Jeśli nie jest wskazana baza kodu, sondy środowiska uruchomieniowego dla zestawu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="b621b-134">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="b621b-135">Jeśli zestaw ma silną nazwę, ustawienie codebase może znajdować się w dowolnym miejscu w lokalnym intranecie lub w Internecie.</span><span class="sxs-lookup"><span data-stu-id="b621b-135">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="b621b-136">Jeśli zestaw jest zestawem prywatnym, ustawienie bazy kodu musi być ścieżką względną do katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b621b-136">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="b621b-137">W przypadku zestawów bez silnej nazwy wersja jest ignorowana, a moduł ładujący używa pierwszego wyglądu \<codebase> wewnątrz \<dependentAssembly> .</span><span class="sxs-lookup"><span data-stu-id="b621b-137">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="b621b-138">Jeśli w pliku konfiguracyjnym aplikacji znajduje się wpis służący do przekierowywania powiązań do innego zestawu, przekierowania będzie miało pierwszeństwo, nawet jeśli wersja zestawu nie jest zgodna z żądaniem powiązania.</span><span class="sxs-lookup"><span data-stu-id="b621b-138">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="b621b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="b621b-139">Example</span></span>

<span data-ttu-id="b621b-140">Poniższy przykład pokazuje, jak określić, gdzie środowisko uruchomieniowe może znaleźć zestaw.</span><span class="sxs-lookup"><span data-stu-id="b621b-140">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b621b-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b621b-141">See also</span></span>

- [<span data-ttu-id="b621b-142">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b621b-142">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="b621b-143">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b621b-143">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="b621b-144">Określ lokalizację zestawu</span><span class="sxs-lookup"><span data-stu-id="b621b-144">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="b621b-145">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="b621b-145">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
