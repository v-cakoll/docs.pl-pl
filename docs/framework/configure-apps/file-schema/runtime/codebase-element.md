---
title: '&lt;codeBase&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3b614546e8ed23cc1a5e169a33fb5878695037ae
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="df304-102">&lt;codeBase&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="df304-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="df304-103">Określa, gdzie znaleźć środowisko uruchomieniowe języka wspólnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="df304-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="df304-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="df304-104">\<configuration></span></span>  
<span data-ttu-id="df304-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="df304-105">\<runtime></span></span>  
<span data-ttu-id="df304-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="df304-106">\<assemblyBinding></span></span>  
<span data-ttu-id="df304-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="df304-107">\<dependentAssembly></span></span>  
<span data-ttu-id="df304-108">\<codeBase ></span><span class="sxs-lookup"><span data-stu-id="df304-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df304-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="df304-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df304-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="df304-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df304-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="df304-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df304-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="df304-112">Attributes</span></span>  
  
|<span data-ttu-id="df304-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="df304-113">Attribute</span></span>|<span data-ttu-id="df304-114">Opis</span><span class="sxs-lookup"><span data-stu-id="df304-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="df304-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="df304-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="df304-116">Określa adres URL, gdzie środowiska uruchomieniowego można znaleźć określonej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="df304-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="df304-117">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="df304-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="df304-118">Określa wersję zestawu, w którym baza kodu dotyczy.</span><span class="sxs-lookup"><span data-stu-id="df304-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="df304-119">Format numeru wersji zestawu jest *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="df304-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="df304-120">Wersja atrybut</span><span class="sxs-lookup"><span data-stu-id="df304-120">version Attribute</span></span>  
  
|<span data-ttu-id="df304-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="df304-121">Value</span></span>|<span data-ttu-id="df304-122">Opis</span><span class="sxs-lookup"><span data-stu-id="df304-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="df304-123">Prawidłowe wartości dla każdej części numer wersji to od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="df304-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="df304-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="df304-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df304-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="df304-125">Child Elements</span></span>  
 <span data-ttu-id="df304-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="df304-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df304-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="df304-127">Parent Elements</span></span>  
  
|<span data-ttu-id="df304-128">Element</span><span class="sxs-lookup"><span data-stu-id="df304-128">Element</span></span>|<span data-ttu-id="df304-129">Opis</span><span class="sxs-lookup"><span data-stu-id="df304-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="df304-130">Definiuje kolekcję dostawców kompilacji używana do kompilowania plików zasobów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="df304-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="df304-131">Może mieć dowolną liczbę dostawcy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="df304-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="df304-132">Konfiguruje wszystkie ustawienia kompilacji używane przez program ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="df304-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="df304-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df304-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="df304-134">Określa element root dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="df304-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df304-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df304-135">Remarks</span></span>  
 <span data-ttu-id="df304-136">Dla środowiska uruchomieniowego do użycia  **\<codeBase >** ustawienia w pliku konfiguracyjnym maszyny lub pliku zasad wydawcy, plik musi również przekierować wersja zestawu.</span><span class="sxs-lookup"><span data-stu-id="df304-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="df304-137">Pliki konfiguracji aplikacji może mieć ustawienie codebase bez przekierowywanie wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="df304-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="df304-138">Po ustaleniu wersji zestawu do użycia, środowisko uruchomieniowe stosuje ustawienia codebase z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="df304-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="df304-139">Jeśli codebase nie jest zaznaczone, środowisko uruchomieniowe sondy dla zestawu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="df304-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="df304-140">Jeśli zestaw ma silną nazwę, ustawienie codebase może być dowolnym w lokalnym intranecie lub Internecie.</span><span class="sxs-lookup"><span data-stu-id="df304-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="df304-141">Jeśli zestaw jest zestaw prywatny, ustawienie codebase musi być ścieżką względną wobec katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df304-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="df304-142">Dla zestawów bez silnych nazw, wersja jest ignorowane, a pierwsze wystąpienie korzysta z modułu ładującego \<codebase > wewnątrz \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="df304-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="df304-143">Jeśli istnieje wpis w pliku konfiguracyjnym aplikacji, który przekierowuje powiązania do innego zestawu, przekierowywanie wyższy priorytet, nawet jeśli wersja zestawu nie odpowiada na żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="df304-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df304-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="df304-144">Example</span></span>  
 <span data-ttu-id="df304-145">Poniższy przykład przedstawia sposób określić, gdzie środowiska uruchomieniowego można znaleźć zestawu.</span><span class="sxs-lookup"><span data-stu-id="df304-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df304-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df304-146">See Also</span></span>  
 [<span data-ttu-id="df304-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="df304-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="df304-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="df304-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="df304-149">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="df304-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="df304-150">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="df304-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
