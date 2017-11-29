---
title: "&lt;codeBase&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b30f1dc3ccade3028c31c57ffdab521802f086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="28f79-102">&lt;codeBase&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="28f79-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="28f79-103">Określa, gdzie znaleźć środowisko uruchomieniowe języka wspólnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="28f79-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="28f79-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="28f79-104">\<configuration></span></span>  
<span data-ttu-id="28f79-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="28f79-105">\<runtime></span></span>  
<span data-ttu-id="28f79-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="28f79-106">\<assemblyBinding></span></span>  
<span data-ttu-id="28f79-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="28f79-107">\<dependentAssembly></span></span>  
<span data-ttu-id="28f79-108">\<codeBase ></span><span class="sxs-lookup"><span data-stu-id="28f79-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f79-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="28f79-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28f79-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28f79-110">Attributes and Elements</span></span>  
 <span data-ttu-id="28f79-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28f79-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28f79-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28f79-112">Attributes</span></span>  
  
|<span data-ttu-id="28f79-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28f79-113">Attribute</span></span>|<span data-ttu-id="28f79-114">Opis</span><span class="sxs-lookup"><span data-stu-id="28f79-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="28f79-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="28f79-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="28f79-116">Określa adres URL, gdzie środowiska uruchomieniowego można znaleźć określonej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="28f79-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="28f79-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="28f79-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="28f79-118">Określa wersję zestawu, w którym baza kodu dotyczy.</span><span class="sxs-lookup"><span data-stu-id="28f79-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="28f79-119">Format numeru wersji zestawu jest *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="28f79-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="28f79-120">Wersja atrybut</span><span class="sxs-lookup"><span data-stu-id="28f79-120">version Attribute</span></span>  
  
|<span data-ttu-id="28f79-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="28f79-121">Value</span></span>|<span data-ttu-id="28f79-122">Opis</span><span class="sxs-lookup"><span data-stu-id="28f79-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="28f79-123">Prawidłowe wartości dla każdej części numer wersji to od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="28f79-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="28f79-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="28f79-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28f79-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28f79-125">Child Elements</span></span>  
 <span data-ttu-id="28f79-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="28f79-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28f79-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28f79-127">Parent Elements</span></span>  
  
|<span data-ttu-id="28f79-128">Element</span><span class="sxs-lookup"><span data-stu-id="28f79-128">Element</span></span>|<span data-ttu-id="28f79-129">Opis</span><span class="sxs-lookup"><span data-stu-id="28f79-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="28f79-130">Definiuje kolekcję dostawców kompilacji używana do kompilowania plików zasobów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="28f79-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="28f79-131">Może mieć dowolną liczbę dostawcy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28f79-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="28f79-132">Konfiguruje wszystkie ustawienia kompilacji używane przez program ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="28f79-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="28f79-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28f79-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="28f79-134">Określa element root dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="28f79-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28f79-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28f79-135">Remarks</span></span>  
 <span data-ttu-id="28f79-136">Dla środowiska uruchomieniowego do użycia  **\<codeBase >** ustawienia w pliku konfiguracyjnym maszyny lub pliku zasad wydawcy, plik musi również przekierować wersja zestawu.</span><span class="sxs-lookup"><span data-stu-id="28f79-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="28f79-137">Pliki konfiguracji aplikacji może mieć ustawienie codebase bez przekierowywanie wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="28f79-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="28f79-138">Po ustaleniu wersji zestawu do użycia, środowisko uruchomieniowe stosuje ustawienia codebase z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="28f79-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="28f79-139">Jeśli codebase nie jest zaznaczone, środowisko uruchomieniowe sondy dla zestawu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="28f79-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="28f79-140">Jeśli zestaw ma silną nazwę, ustawienie codebase może być dowolnym w lokalnym intranecie lub Internecie.</span><span class="sxs-lookup"><span data-stu-id="28f79-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="28f79-141">Jeśli zestaw jest zestaw prywatny, ustawienie codebase musi być ścieżką względną wobec katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28f79-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="28f79-142">Dla zestawów bez silnych nazw, wersja jest ignorowane, a pierwsze wystąpienie korzysta z modułu ładującego \<codebase > wewnątrz \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="28f79-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="28f79-143">Jeśli istnieje wpis w pliku konfiguracyjnym aplikacji, który przekierowuje powiązania do innego zestawu, przekierowywanie wyższy priorytet, nawet jeśli wersja zestawu nie odpowiada na żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="28f79-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f79-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="28f79-144">Example</span></span>  
 <span data-ttu-id="28f79-145">Poniższy przykład przedstawia sposób określić, gdzie środowiska uruchomieniowego można znaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="28f79-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28f79-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28f79-146">See Also</span></span>  
 [<span data-ttu-id="28f79-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="28f79-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="28f79-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28f79-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="28f79-149">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="28f79-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="28f79-150">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="28f79-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
